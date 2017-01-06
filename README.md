# NCYU-BRD-ZhaoYan..github.io
  
  
## 一、	個人特質及生活態度

我的個性溫和、內向、樸實，是個很好溝通的人。每當遇到沮喪或瓶頸，我都會以積極正向的態度去面對。在學校生活裡，我以親切有禮貌的態度與老師同學相處，人際關係十分融洽，也從中獲益良多。我對於生活的態度就是「不管對或錯只要對自己負責」。

## 二、	求學歷程

在高一寒假時加入圖書館志工，為民眾服務，體驗公務員的職場生活，在升高二時參加監理站的小志工，學習公務人員基本的文書處理。約在三月去成功大學一日的教育參訪之旅，又在七月參加清華大學物理系辦的「輻射與原子核能隱形能量知識深耕」科學營。
    上國立嘉義大學後，我積極參與系上的活動，大採、小採等活動。開始投入對生物的認識，雖說不是很懂或該說生物是越去認識他越是不了解他，這也是生物迷人之處。我也參與學校的社團-水上活動社。從不會游泳到會游泳，積極學習其他水上活動，例如水球、獨木舟、救生等等。現在擔任副社長，努力推廣水上活動給學校全體同學認識。讓他們對於水域安全及水上活動有更深一成的認識。



大家好～歡迎來到阿延的繁星夜空------第八夜


晚安各位 謝謝你們的閱讀與支持
祝你們有個好眠，明天又是美好的一天
期待下次與你的分享
若有悄悄話歡迎隨時密我，這裡是專屬你的天空
阿延的繁星夜空下次見 掰掰

[參考老師的網址]https://gist.github.com/mutolisp/d613948fbf91ae29a532dc672b6f36f3

## data transformation

# 使用 dplyr 和 tidyr
# install dplyr and tidyr first
install.packages(c('dplyr', 'tidyr', 'dtplyr'))
require(dplyr)
require(tidyr)
require(dtplyr)
# install data sets
devtools::install_github('rstudio/EDAWR')
# install_github 可以直接從 github 安裝
# 例如，若有個 r package 放在
http://github.com/mutolisp/twmap 上，就可以用下列的方式安裝

devtools::install_github('mutolisp/twmap')

# fundamental syntax of dplyr
# dplyr "tibble" (tbl) format is more readable than built-in data.frame
# tbl 格式
---R
iris.tbl <- dplyr::tbl_df(iris)
iris.tbl
---
# 簡單看一下 tbl (類似 summary)
---R
dplyr::glimpse(iris.tbl)
---
# 另一個 dplyr 特殊的符號 %>%
# 把左邊的 object 當成是右邊 function 的
# 第一個參數(argument)
# ex: x %>% f(y) ==> f(x, y)

# 實際的例子:
iris %>% group_by(Species) %>%
  summarise(avg = mean(Sepal.Length))

dplyr::group_by(iris, Species)

# dplyr::summarise() 
summarise(mtcars, mean(hp))

# 從 vignettes 中學習 dplyr
browseVignettes(package = "dplyr")

install.packages('nycflights13')
library(nycflights13)
dim(flights)

## dplyr verbs 範例

# 假設我們要把 1 月 1 日的航班資料全部撈出來，
# 如果用 data frame 該怎麼做呢？
# 先把 tibble format 存成 dataframe 格式
flights.df <- as.data.frame(flights)

flights0101.df <- flights.df[flights.df$month == 1 & flights.df$day == 1,]

# 若使用 filter 篩選資料
filter(flights, month == 1, day == 1, 
       origin == 'JFK', dest == 'MIA')
# 你也可以使用其他的邏輯判斷，像是 &, | 或 boolean operators

# 把一月份或二月份由 JFK 機場出發的航班找出來
filter(flights, month == 1 | month == 2, 
       origin == 'JFK')

# slice 去切分 subsets
slice(flights, 1:10)

# arrange 排序
arrange(flights, year, month, day)

# 也可以搭配 desc 反序排列
arrange(flights, year, desc(month), desc(day))

# select 來選擇特定欄位
select(flights, month, day, origin, dest)

# 也可以使用分號選擇區間
select(flights, year:origin)

# rename
flights <- rename(flights, destination = dest)
flights <- rename(flights, dest = destination)

# distinct 
distinct(flights, origin)
# 這個和傳統 R 的 unique 相同
unique(flights$origin)

# distinct 也可以結合多個欄位
distinct(flights, origin, dest, carrier)

# mutate 新增欄位
flights.m <- mutate(flights,
                    gain = arr_delay - dep_delay,
                    speed = distance / air_time * 60)

select(flights.m, carrier, gain, speed)

by_tailnum <- group_by(flights, tailnum)
delay <- summarise(by_tailnum,
                   count = n(),
                   dist = mean(distance, na.rm = TRUE),
                   delay = mean(arr_delay, na.rm = TRUE))
delay <- filter(delay, count > 20, dist < 2000)

# CWB data
cwb10 <- fread('~/Downloads/cwb2006-2015/C0M530.txt',
               na.strings = c('-9991', '-9996', '-9997',
                              '-9998', '-9999'))
setnames(cwb10, 1:9, c('stno','yyyymmddhh','PS01','TX01','RH01','WD01','WD02','PP01','SS01'))

cwb10[, timestamp := as.POSIXct(strptime(yyyymmddhh, '%Y%m%d%H'))]

# 新增年的欄位
cwb10[, year := year(timestamp)]
# 新增月的欄位
cwb10[, month := month(timestamp)]
# 新增日的欄位
cwb10[, day := mday(timestamp)]


cwb10.tbl <- tbl_df(cwb10)
f1 <- filter(cwb10.tbl, year == 2006)
group_by(f1, year, month) %>% 
  summarise(Tavg = mean(TX01, na.rm = T),
            Precp = sum(PP01, na.rm = T))
