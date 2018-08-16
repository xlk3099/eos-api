## get_info 
返还blockchain详细信息，比如
1. 服务器版本
2. 当前区块最高高度
3. 当前不可逆高度
4. 最新block 
    1. block id （暂时不知道啥用，估计mongoDB id？）
    2. 挖到时间
    3. producer（谁挖的）

## get_block
给定block number 或者id 返回该block具体信息
1. 前一个block_id 或者说parent_id
2. timestamp
3. tx mroot
4. action mroot
5. block mroot
6. producer （幸运儿）
7. schedule_version? 不知道有啥用
8. new_producers ? 不懂，还能有new producers 指下一个么？
9. producer 签名 防伪
10. confirmed? 没看出用途
11. tx 列表  -- 跟eth 类似，返回blocks的时候会返回transaction list
    1. 状态：已执行未执行
    2. cpu使用：按微秒计算
    3. 

## get_transaction
感觉很乱，需要更多时间来理解可挖掘信息
> ./cleos get transaction 715acb3ea0cb09242d4114fc4e87f5942208ffc4f3936369101b7ae5f06f9527

见参考sample

## get_block_header_state
坑爹 API, 本机跟BP都不能用...暂时不管

## get_account
信息比较齐全
比较感兴趣的fields
1. 创建时间
2. cpu 使用情况
3. ram usage
4. network usage
5. 投票情况

## get abi
给定account 名
查看其所有的abi
不是很理解
> > ./cleos get abi eosshadows

## get code 
照官方文档没能成功运行例子
不是很着急，V2候选

## get raw code and abi
同上

## get_table_rows
没用明白，可能对拿token的排名有帮助
但是scope是account，所以可能性不大

## get_currency_balance
同上 没大明白

## abi_json_to_bin
顾名思义，没啥好讲的

## abi_bin_to_json
顾名思义，没啥好讲的

## get_required_keys
对浏览器开发没啥帮助

## get_currency_stats
暂时没看到用处

## get_actions
非常有用，get_account recent actions

> ./cleos get actions jeffzhengzrj -1 -20 --full

## get_controlled_accounts

返还该账号控制的子账号
curl --request POST \
  --url http://127.0.0.1:8888/v1/history/get_controlled_accounts \
  --data '{"controlling_account":"eosio"}'

```json
{"controlled_accounts":["eoshappyvote","eosio.bpay","eosio.msig","eosio.names","eosio.ram","eosio.ramfee","eosio.saving","eosio.stake","eosio.token","eosio.unregd","eosio.vpay","eosvrtokenss","gm2dimrqgige","nvoyiooiyovn","stoponnopots","testtodelete","toohottohoot"]}
```

## get_key_accounts
给定pub key 返回account名么？没试...
