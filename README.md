#题目描述：
预测股票市场个股的涨跌，以及从中发现规律，在合适的时候买入卖出股票，能够有机会获取巨大的利益。华尔街以及中国兴起的中国对冲基金、新型证券公司，包括一些知名的个人投资经理和操盘手，正在通过这种方式，在股票市场套利，实现财富自由。该题目提供给选题小组这样的机会，我们提供近300家上市公司的在某段时间内的按日为单位的股价数据，要求选题小组通过对给定公司集合特定时间内股价走势的学习，生成模型，用生成的模型判断未来一段时间内该集合内每家公司的股票走势，从而生成以买卖两种基本操作构成的交易序列。选题小组的目的是使得模型所生成的交易序列在未来的一段时间内，以按月为单位的，所有公司的夏普比率（Sharpe Ratio），即平均收益/平均均差 最大化。


#数据及提交格式：
##训练数据：近300家上市公司2011-04-01到2016-06-30 的按日股价数据，训练数据位置：./stockData/。
        每一行格式：date：日期\tclose：收盘价\tma5：5日均价\tp_change：涨跌幅
##提交数据：模型对于近300家上市公司在2016-07-01到2017-01-31预测的序列。
        具体格式：每家公司一行结果，共298行
        每一行格式：公司id\tlong|||2016-07-01|||2016-07-02\tshort|||2016-07-03|||2016-07-04
        其中long表示先买后卖，short表示先卖后买。允许对一家公司重复同样的交易。同一次交易的买卖时间不能相同。


#评价指标：
2016-07-01到2017-01-31期间所有公司的夏普比率（Sharpe Ratio），即平均收益/平均均差


#提交时间：
每隔一周的周二7PM，将提交数据发送至wangcgpeking@gmail.com, 并且抄送给雷鸣老师：ming.lei@gmail.com



#模型建议：
利用 深度学习（基本全连接神经网络，或CNN, LSTM）分类器预测某只股票的涨跌幅。模型的输入特征向量可以为每只股票在特定时间内（长度可以为1-2周）股价值，以及300只股票的对应时间内的平均值。然后利用这段时间之后（间隔可以为1-5周）股票涨跌的情况作为输入特征向量的标签，从而完成某种分类器的训练。选取最好的分类器提交，进行测试。
另外，如果发现直接去优化夏普比率比较困难，因为是除法的形式，也可以尝试变形为优化|平均收益-平均均差|，不完全等价于夏普比率，但是优化方向是一致的。
