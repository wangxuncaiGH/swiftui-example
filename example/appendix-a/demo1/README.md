了解 Swift 和 SwiftUI 中的属性包装器
===

SwiftUI 严重依赖属性包装器，以使我们的代码更易于阅读，编写和维护，但是如果您从未使用过它们，您可能会想知道所有 `@` 和 `$` 符号的来源 - 乍一看它们似乎很陌生。

尽管自从 `Swift 5.1` 引入属性包装器以来，它是 `Swift` 的一项常规功能，但它们在 `SwiftUI` 中尤为常见 -您 会看到 `@Published`，`@ObservedObject`，`@EnvironmentObject`等，所有这些都是为了减少模板的数量 在我们的代码中。

在接下来的几章中，我们将详细介绍每个 `SwiftUI` 的属性包装器，但只需简要介绍一下这些基础知识即可：

- 一些属性包装器使我们可以获得原本不可能的效果，例如 `@State` 允许我们修改结构体中的属性的方式。
- 某些属性包装程序明确要求您在其他地方做额外的工作，如果未完成，则可能会使您的应用程序崩溃。 例如，`@FetchRequest`希望您提前将 `Core Data` 管理的对象上下文放入环境中。
- 您一次只能应用一个属性包装器，这意味着 `@ObservedObject @Binding var value = SomeClass()` 是不允许的。
- 即使某些属性包装看起来很相似（看着您，`@Environment` 和 `@EnvironmentObject`!），它们也有所不同，因此，请务必正确使用它们。
- 您可以根据需要创建自己的属性包装器，但这不是使用 SwiftUI 所必需的。

这涵盖了基础知识，但是要真正了解这些属性包装程序是如何工作的，有必要对它们进行逐一研究。