# 业务资料约定

时间是相对运行纪元的分钟，区间均左闭右开；known_at与confirmed_at为资料可见时刻。压力MPa、温度摄氏度、load为百分比。null为缺测。状态与事故记录彼此独立，未确认时段不自动作为正常训练。

每行id在该表内唯一，文件顺序不代表业务事件顺序。清单schema=1，各表登记文件名、字节长度、SHA256、行数及完整字段集合，未知版本或内容变化应重新登记。金额及测量数值均为独立资料，不代表任何现实机构的经营数据。

- observations：id、minute、load、pressure、temperature、vibration。
- states：id、start、end、regime、known_at。
- incidents：id、start、end、confirmed_at。
- training：id、start、end、confirmed_at。

normal与boundary是相互独立的资料包，不能直接拼接重复id。引用字段按本项目domain.py的REFERENCES登记。读取检查只检查完整性、身份及这些直接引用，不替代领域分析中的可识别性、时点可见性或可行性判断。
