auto实际意义就是可以自动计算出数据类型。

我们可以使用，但不要滥用。
一方面，使用auto可以给我们带来方便，如改变api的返回值，客户端不需要改。但同时也会带来一些很难处理的问题，比如我们默认api返回值是string，我们就会调用string的相关函数，但如果改了返回值后，客户端不知道，但string的函数用不了了，会报错。

当变量们超长的时候，我们适当使用auto。对于int string等，不要用auto，那样会降低代码可读性。