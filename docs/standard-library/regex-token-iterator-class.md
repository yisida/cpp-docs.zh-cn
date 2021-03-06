---
description: 了解详细信息： regex_token_iterator 类
title: regex_token_iterator 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 752ff44864b435100bacb83250a5c6a792cab502
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243882"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator 类

子匹配项的迭代器类。

## <a name="syntax"></a>语法

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>parameters

*BidIt*\
子匹配项的迭代器类型。

*Elem*\
要匹配的元素的类型。

*RXtraits*\
元素的特征类。

## <a name="remarks"></a>备注

类模板描述常量向前迭代器对象。 从概念上讲，它承载 `regex_iterator` 对象，并用于搜索字符序列中正则表达式的匹配项。 它提取 `sub_match<BidIt>` 类型的对象，这些对象表示由每个正则表达式匹配项的存储向量 `subs` 中的索引值标识的子匹配项。

-1 索引值指定在上一个正则表达式匹配项末尾后立即开始（如果不存在上一个正则表达式匹配项，则为从字符序列的起始处开始）的字符序列，并扩展到但不包含当前正则表达式匹配项的第一个字符（如果不存在当前匹配项，则扩展到字符序列末尾）。 任何其他索引值 `idx` 指定承载于 `it.match[idx]`中捕获组的内容。

### <a name="members"></a>成员

|成员|默认值|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|构造迭代器。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[difference_type](#difference_type)|迭代器差异的类型。|
|[iterator_category](#iterator_category)|迭代器类别的类型。|
|[变为](#pointer)|指向一个匹配的指针的类型。|
|[reference](#reference)|对子匹配项的引用的类型。|
|[regex_type](#regex_type)|要匹配的正则表达式类型。|
|[value_type](#value_type)|子匹配项的类型。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator！ =](#op_neq)|比较不相等的迭代器。|
|[操作员](#op_star)|访问指定的子匹配项。|
|[operator + +](#op_add_add)|递增迭代器。|
|[operator = =](#op_eq_eq)|比较迭代器是否相等。|
|[operator->](#op_arrow)|访问指定的子匹配项。|

## <a name="requirements"></a>要求

**标头：**\<regex>

**命名空间:** std

## <a name="example"></a>示例

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="regex_token_iteratordifference_type"></a><a name="difference_type"></a> regex_token_iterator：:d ifference_type

迭代器差异的类型。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>备注

该类型是 `std::ptrdiff_t` 的同义词。

## <a name="regex_token_iteratoriterator_category"></a><a name="iterator_category"></a> regex_token_iterator：： iterator_category

迭代器类别的类型。

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>备注

该类型是 `std::forward_iterator_tag` 的同义词。

## <a name="regex_token_iteratoroperator"></a><a name="op_neq"></a> regex_token_iterator：： operator！ =

比较不相等的迭代器。

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>parameters

*然后*\
要进行比较的迭代器。

### <a name="remarks"></a>备注

成员函数返回 `!(*this == right)`。

## <a name="regex_token_iteratoroperator"></a><a name="op_star"></a> regex_token_iterator：： operator *

访问指定的子匹配项。

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>备注

成员函数返回一个 `sub_match<BidIt>` 对象，该对象表示由索引值 `subs[pos]`标识的捕获组。

## <a name="regex_token_iteratoroperator"></a><a name="op_add_add"></a> regex_token_iterator：： operator + +

递增迭代器。

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>备注

如果存储的迭代器 `it` 是序列末尾迭代器，则第一个运算符将存储的值 `pos` 设置为 `subs.size()` 的值（从而生成序列末尾迭代器）。 否则，运算符递增存储的值 `pos`；如果结果等于值 `subs.size()`，则它将存储的值 `pos` 设置为零，并递增存储的迭代器 `it`。 如果递增存储的迭代器让它不等于序列结尾迭代器，则运算符不会进一步执行操作。 否则，如果前面匹配项的结尾位于字符序列的结尾，则运算符将 `pos` 的存储的值设置为 `subs.size()`。 否则，运算符重复递增存储的值 `pos`，直到 `pos == subs.size()` 或 `subs[pos] == -1`（从而确保其中一个索引值为 -1 时，迭代器的下一次取消引用将返回字符序列的结尾）。 在所有情况下，运算符都会返回对象。

第二个运算符生成对象的副本，递增对象，然后返回副本。

## <a name="regex_token_iteratoroperator"></a><a name="op_eq_eq"></a> regex_token_iterator：： operator = =

比较迭代器是否相等。

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>parameters

*然后*\
要进行比较的迭代器。

### <a name="remarks"></a>备注

成员函数返回 `it == right.it && subs == right.subs && pos == right.pos`。

## <a name="regex_token_iteratoroperator-gt"></a><a name="op_arrow"></a> regex_token_iterator：： operator-&gt;

访问指定的子匹配项。

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>备注

成员函数返回一个指向 `sub_match<BidIt>` 对象的指针，该对象表示由索引值 `subs[pos]`标识的捕获组。

## <a name="regex_token_iteratorpointer"></a><a name="pointer"></a> regex_token_iterator：:p ointer

指向一个匹配的指针的类型。

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>备注

类型是 `sub_match<BidIt>*` 的同义词，其中 `BidIt` 是模板参数。

## <a name="regex_token_iteratorreference"></a><a name="reference"></a> regex_token_iterator：： reference

对子匹配项的引用的类型。

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>备注

类型是 `sub_match<BidIt>&` 的同义词，其中 `BidIt` 是模板参数。

## <a name="regex_token_iteratorregex_token_iterator"></a><a name="regex_token_iterator"></a> regex_token_iterator：： regex_token_iterator

构造迭代器。

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>parameters

*1*\
要匹配的序列的开头。

*时间*\
要匹配的序列的结尾。

*&*\
匹配项正则表达式。

*果*\
匹配标志。

### <a name="remarks"></a>备注

第一个构造函数将构造序列末迭代器。

第二个构造函数将构造一个对象，其存储的迭代器 `it` 初始化为 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`，其存储的向量 `subs` 承载恰好一个整数（值为 `submatch`），并且其存储的值 `pos` 为零。 注意：对于每个成功的正则表达式匹配项，生成的对象将提取由索引值 `submatch` 标识的子匹配项。

第三个构造函数将构造一个对象，其存储的迭代器 `it` 初始化为 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`，其存储的向量 `subs` 承载构造函数参数 `submatches`的一个副本，并且其存储的值 `pos` 为零。

第四个构造函数将构造一个对象，其存储的迭代器 `it` 初始化为 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`，其存储的向量 `subs` 承载构造函数参数 `N` 指向的 `submatches`值，并且其存储的值 `pos` 为零。

## <a name="regex_token_iteratorregex_type"></a><a name="regex_type"></a> regex_token_iterator：： regex_type

要匹配的正则表达式类型。

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>备注

typedef 是 `basic_regex<Elem, RXtraits>`的同义词。

## <a name="regex_token_iteratorvalue_type"></a><a name="value_type"></a> regex_token_iterator：： value_type

子匹配项的类型。

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>备注

类型是 `sub_match<BidIt>` 的同义词，其中 `BidIt` 是模板参数。

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)\
[regex_constants 类](../standard-library/regex-constants-class.md)\
[regex_error 类](../standard-library/regex-error-class.md)\
[\<regex> 函数](../standard-library/regex-functions.md)\
[regex_iterator 类](../standard-library/regex-iterator-class.md)\
[\<regex> 运算符](../standard-library/regex-operators.md)\
[regex_traits 类](../standard-library/regex-traits-class.md)\
[\<regex> typedef](../standard-library/regex-typedefs.md)
