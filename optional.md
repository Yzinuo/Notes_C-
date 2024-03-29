笔记:
optional用来处理可能存在也可能不存在数据的方法。
C++17
#include <optional>
std::optional<type> function(param){statement; return type;}
auto result = function();
1: result.has_value()判断数据是否存在, 通过result.value()获取数据
2: result.value_or(xxx)其中xxx作为默认值，如果存在数据返回数据，不存在返回xxx
3:通过if (result)判断数据是否存在

注: 使用场景—目标值可能存在也可能不存在，比如读取文件并返回内容，可能读取成功有数据，读取成功无数据，读取不成功。