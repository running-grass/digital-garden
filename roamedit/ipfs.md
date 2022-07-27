ipfs
---------------------------

IPFS
   :PROPERTIES:
   :CUSTOM_ID: ipfs
   :END:

- 星际文件系统，一种文件传输协议，对标[[HTTP]]
- 一个基于区块链的分布式文件存储系统

为了使更多地人参与到这个分布式系统中来，在IPFS智商有一个激励系统[[Filecoin]]，通过提供存储和检索的服务，来证明工作量。盘活整个平台
* 通过提供存储和检索的服务，来证明工作量。盘活整个平台
* 可以类似[[Git]]的版本功能 * 直接使用可以用来存放文件 *
* 在add的时候可以通过-s参数来控制block的大小，默认256

当在本地添加一个文件之后，会把这个文件的hash公布出去，便于其它节点的检索，但是文件本身还是存放在本地的，当有人通过其它的节点或网关访问的时候，才会从本地传输一份拷贝过去，至此，这个文件便已经脱离了控制。不能人为的删除，只能等待这个文件成为冷文件之后，在清理空间的时候，被删掉，但是这个hash会一直存在网络中。所以一旦这个hash泄露，或者被随意蒙到，便一发不可收拾，而其宣称的永久存储和隐私性更是无从谈起。因为冷文件会被删掉，而一旦知道了hash便会被多处下载，无法删除。也没有加密和管理方案。适合作为bt分享用。
    * 落地应用 * brave 隐私浏览器 * [[IPNS]] + 国内可用网关 *
https:_ipfs.leiyun.org/ * https:_hardbin.com/ * 可用网关获取