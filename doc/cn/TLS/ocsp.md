---
score: 30
---

# OCSP 服务

**OCSP（Online Certificate Status Protocol）** 是一种用于获取 X.509 数字证书有效性状态的网络协议。

例如，当用户尝试访问一家银行的网站时，其浏览器会通过 OCSP 向证书颁发机构（CA）发送一个请求，以确认该网站的 SSL 证书是否仍然有效且未被撤销。如果证书被撤销，比如因为密钥被泄露，那么 OCSP 的应答会告知浏览器，随后浏览器将阻止用户访问该网站，保护用户免遭欺诈或数据泄露的风险。

然而，**OCSP 服务本身也可能面临延迟和隐私问题** ，因为它需要在用户访问安全网站前实时检查证书状态。为了解决这些问题，出现了 OCSP Stapling 技术，该技术允许网站直接在 TLS 握手时提供一个证书状态的时间戳副本，减少了对 CA 的直接请求，从而提高了效率并增强了隐私。

并非所有客户端都默认启用 OCSP，例如基于 OpenSSL 的 curl 客户不启用 OCSP，而基于 Windows schannel 的则启用，且 Google Chrome 自 2012年以来因 [延迟和隐私问题](https://www.imperialviolet.org/2012/02/05/crlsets.html)  而停用OCSP，转而采用其 [自己的更新机制](https://www.zdnet.com/article/chrome-does-certificate-revocation-better/) 同步证书撤销信息。

🔗 [OCSP - Wikipedia](https://zh.wikipedia.org/wiki/%E5%9C%A8%E7%BA%BF%E8%AF%81%E4%B9%A6%E7%8A%B6%E6%80%81%E5%8D%8F%E8%AE%AE) | #OCSP #数字证书 #网站安全 #SSL验证 #互联网安全 #kb
