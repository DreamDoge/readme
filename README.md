
# 说明
1. 本程序为命令行程序，需在命令行中执行。
2. 如果默认参数和你要设置的参数一致，可不用设置
3. 预售脚本，最多可设置2个调用者，抢币不限制调用者

# 参数说明
```
Options:
  -n, --node <websocket>          设置节点链接 (default: "wss://bsc-ws-node.nariox.org:443")
  -k, --key <private key>         设置GAS钱包私钥
  -b, --bot <bot address>         设置专属合约地址
  -t0, --token0 <pair>            设置交易对代币 (default: "BNB"),目前仅支持BNB，USDT，BUSD
  -t1, --token1 <target address>  设置目标代币
  -a, --amount <amount>           设置购买数量
  -c, --count <amount>            设置购买次数 (default: 1)
  -bp, --burn <burn percent>      设置可接受燃烧比例 (default: 100)
  -sp, --sell <sell percent>      设置测试卖出比例 (default: 1)
  -gp, --gasPrice <gasPrice>      设置gas price (default: "5")
  -gl, --gasLimit <gasLimit>      设置gas limit (default: 10000000)
  -i, --interval <interval>       设置交易提交间隔时间(毫秒) (default: 2000) 仅用于燃烧模式
  -fc, --failCount <failCount>    设置最大失败次数 (default: 120) 仅用于燃烧模式
  -st, --startTime <startTime>    设置开始时间(比真正预售时间稍微早3秒，YYYY-MM-DD hh:mm:ss)，若不设置则是立即开始。 仅用于燃烧模式

```
## 轮询样例
轮询的gas费要设置高一些，才能优先成交。要保证gas钱包余额大于gasprice*gaslimit乘积

macos
```
./Main-macos  \
-n wss://bsc-ws-node.nariox.org:443 \
-k gas钱包私钥 \
-b 0xc11d2054AAC9bF0198dA930f05b1c25662d9FA98 \
-t0 BNB \
-t1 0x36c77700eff806BaE46548DA06B442cB37698c6A \
-a 0.1 \
-c 1 \
-bp 60 \
-sp 1 \
-gp 21 \
-gl 10000000 \
loop
```

windows
```
C:\Users\Administrator\Downloads\Main-win.exe -n wss://bsc-ws-node.nariox.org:443 -k gas钱包私钥 -b 0xc11d2054AAC9bF0198dA930f05b1c25662d9FA98 -t0 BNB -t1 0x36c77700eff806BaE46548DA06B442cB37698c6A -a 0.1 -c 1 -bp 60 -sp 1 -gp 21 -gl 10000000 loop
```

## 燃烧样例
默认gas费即可

macos
```
./Main-macos.exe  \
-n wss://bsc-ws-node.nariox.org:443 \
-k gas钱包私钥 \
-b 0xc11d2054AAC9bF0198dA930f05b1c25662d9FA98 \
-t0 BNB \
-t1 0x36c77700eff806BaE46548DA06B442cB37698c6A \
-a 0.1 \
-c 1 \
-bp 60 \
-sp 1 \
-gp 5 \
-gl 10000000 \
burn \
-i 20000 \
-fc 1
```

windows
```
C:\Users\Administrator\Downloads\Main-win.exe -n wss://bsc-ws-node.nariox.org:443 -k gas钱包私钥 -b 0xc11d2054AAC9bF0198dA930f05b1c25662d9FA98 -t0 BNB -t1 0x36c77700eff806BaE46548DA06B442cB37698c6A -a 0.1 -c 1 -bp 60 -sp 1 -gp 21 -gl 10000000 burn -i 20000 -fc 1
```

# 预售基本参数
```
  -n, --node <websocket>          设置节点链接 (default: "wss://bsc-ws-node.nariox.org:443")
  -k, --key <private key>         设置钱包私钥
  -a, --amount <amount>           设置购买数量
  -gp, --gasPrice <gasPrice>      设置gas price (default: "5")
  -gl, --gasLimit <gasLimit>      设置gas limit (default: 10000000)
  -ma, --mainAccount <mainAccount>    设置主账户
  -i, --interval <interval>           设置交易提交间隔时间(毫秒) (default: 2000)
  -fc, --failCount <failCount>        设置最大失败次数 (default: 3)
  -pt, --presaleToken <presaleToken>  设置预售地址
  -st, --startTime <startTime>        设置开始时间(比真正预售时间稍微早3秒，YYYY-MM-DD hh:mm:ss)，若不设置则是立即开始
```

## Feg预售平台
macos
```
./Main-macos -k 调用者私钥 \
-a 0.001 \
fegPresale \
-ma 0xB1B12B99d88BcB47BcD3Ae8d086324C9B2260649 \
-i 20000 \
-pt 0xDce1bcbE36633275f3C597Bd4Ee142d7654676de \
-st "2021-10-15 18:18:00"
```
windows
```
C:\Users\Administrator\Downloads\Main-win.exe -a 0.001 fegPresale -ma 0xB1B12B99d88BcB47BcD3Ae8d086324C9B2260649 -i 20000 -pt 0xDce1bcbE36633275f3C597Bd4Ee142d7654676de -st "2021-10-15 18:18:00"
```

## dxsale/pinksale预售平台
macos
```
./Main-macos -k 调用者私钥 \
-a 0.001 \
presale \
-ma 0xB1B12B99d88BcB47BcD3Ae8d086324C9B2260649 \
-i 20000 \
-pt 0xDce1bcbE36633275f3C597Bd4Ee142d7654676de \
-st "2021-10-15 18:18:00"
```
windows
```
C:\Users\Administrator\Downloads\Main-win.exe -a 0.001 presale -ma 0xB1B12B99d88BcB47BcD3Ae8d086324C9B2260649 -i 20000 -pt 0xDce1bcbE36633275f3C597Bd4Ee142d7654676de -st "2021-10-15 18:18:00"
```
