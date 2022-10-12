---
title: "监听一个DOM元素的出现"
date: 2022-06-13T14:22:02+08:00
tags: 
  - javascript
  - MutationObserver
  - Dom 
  - react
  - hooks

draft: false
---

最近写浏览器插件碰到一个需求，需要操作一个页面上的dom，但是dom是被异步加载的，所以需要监听这个DOM的出现。
<!--more-->

## 实现思路
利用WebAPI中的`MutationObserver`对象来做监听。

## 函数实现

```javascript
/**
 * 等待指定元素出现的监听器
 * @param selector css选择器
 * @param timeout 超过超时时间后会返回reject,默认30000(30s)
 * @param doc 可以指定document，多用于iframe操作，默认为当前的document
 * @returns 成功后返回一个指定元素的Promise和取消函数
 */
export function waitForElm(selector: string, timeout?: number, doc?: Document) {
  const scopedDoc = doc ? doc : document
  let observer: MutationObserver | null
  let outRejectFn: ((reason?: any) => void) | null

  const promise = new Promise<Element>((resolve, reject) => {
    const el = scopedDoc.querySelector(selector)
    if (el) {
      return resolve(el);
    }

    outRejectFn = reject

    observer = new MutationObserver(mutations => {

      for (const mutation of mutations) {
        const targetEl = (mutation.target.parentElement ?? scopedDoc)?.querySelector(selector)
        if (targetEl) {
          outRejectFn = null
          resolve(targetEl);
          observer?.disconnect();
          return
        }
      }
    });

    observer.observe(scopedDoc, {
      childList: true,
      subtree: true
    });


    setTimeout(() => {
      outRejectFn = null
      reject('超时');
      observer?.disconnect();
    }, timeout || 30000)

  });

  return {
    promise,
    abort: () => {
      outRejectFn && outRejectFn('主动取消')
      outRejectFn = null
      observer?.disconnect();
    }
  }
}

```

## React的Hooks封装

```javascript
/**
 * 等待指定元素出现的hooks
 * @param selector css选择器
 * @param timeout 超过超时时间后会返回reject,默认30000(30s)
 * @param doc 可以指定document，多用于iframe操作，默认为当前的document
 * @returns 成功后返回一个指定元素的Promise和取消函数
 */
export function useWaitForElm(selector: string, timeout?: number, doc?: Document) {
  const [elm, setElm] = useState<Element | null>(null)

  useEffect(() => {
    const { promise, abort } = waitForElm(selector, timeout, doc)
    try {
      promise.then((el) => {
        setElm(el)
      })
    } catch {
    } finally {
      return abort
    }
  }, [])

  return elm
}

```