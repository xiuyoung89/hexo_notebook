# EOS 投票机制总结

## 小结-eos本身的投票机制是这样的：

1. 投票前需要抵押eos，比如抵押了90个eos，就有90张票。然后可以投给最多30个生产者。如果给30个生产者都投票了，那么每个生产者都获得90张选票。不能设置给这个生产者6张，给那个生产者20张。
2. 如果你之前给生产者A投票了，然后你又继续抵押了20个EOS，那么会自动给生产者A加上20张选票。相当于抵押的时候，看你有没有投票过，如果投票过，就把你投票的生产者票数都加上新增抵押的数目。
3. eos的选票有权重，权重计算公共为：抵押代币数量 * 2 ^ (weeks_since_launch/weeks_per_year)。改变抵押代币的数量，投票权重会自动变化。
4. 投票权重有半衰期。