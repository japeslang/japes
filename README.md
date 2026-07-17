# The Japes Programming Language

This is the primary repository for the Japes Programming Language. Japes is designed to be a portable programming language with aspects of C#, C++, Perl, and PHP. Its initial design will be for the .NET framework, and it is primarily an object-oriented language. Its companion, J4, will serve as a macro preprocessor. Planned features include:

- Support for both modern, JIT-based runtimes (like .NET or Parrot) and native architectures.
- Transpilation/Static Recompilation capability in the output engine.
- Support for both dynamic type generics (?[...]) and SFINAE (C++-style, ![...]) templates.
- Robust systems programming support.

It is meant to be C++ with properties, or maybe C# with compile-time metaprogramming. Although compiler bootstrap will occur on .NET, it is thought that JVM, the Zend Engine, HiphopVM, Webassembly, and Parrot may also be possible targets. Support for native architectures is also planned (perhaps by using LLVM); in fact, freestanding code is planned on these architectures. In some cases, particularly constrained targets may nonetheless be able to execute this code with a little assistance, so support for transpilation and static recompilation plugins are also planned. Thus, a highly flexible build pipeline is required.

Many data structures in Japes (including arrays, numbers, characters, and boolean values) fall into a class of objected called tensors. This allows for generic indexed operations on those who implement `japes.util.IConstTensor` and its descendant interfaces, which are designed to provide a rich set of operations. A generic, extensible basis for the type algebra will be developed; `japes.math.INumber?[T]` exposes a number abstractly, for instance. We also include `japes.math.ILogic?[T]` to abstractly represent fuzzy or non-binary logic; the type `japes.Boolean` is itself an `ILogic?[T]`. `japes.text.IString?[T]` is more rigoriously defined than `japes.util.IVector?[T]`, and the same is true of `japes.math.IVector?[T]`. There's rich support for unmanaged memory operations, and abstractions to help support interaction with remote, losely coupled memory spaces. On platforms where one is available, you can take control of some aspects of allocation itself.

The desired result is an ecosystem that can be adapted to many disparate ecosystems. To tie them all together, Japes defines a high-level intermediate representation (HIR) that it can use to encode language support where it might not otherwise exist. For instance, most of the above environments do not support compile-time templates of any kind, so these templates are exported with the binary. It may be possible to instantiate templates at runtime using this method. Where a JIT or native Japes implementation can't be supported, translation facilities can used to help bridge the gap.

## Licensing

The source code associated with this project are licensed under the [GNU General Public License version 3](LICENSE.txt); in order to solve the question about linking against the standard library or the toolchain, [the Classpath exception](claspath.md) is appended to it. You should have recieved a copy of both with this file. 

## This is a Virtual Monorepo (VMR)

Instead of using the monorepo proper, this project's organization is inspired by [dotnet](https://github.com/dotnet). Individual repoitories under this organization will correspond to its own repository so that concerns may be more easily separated. This repo is called `japeslang/japes` and reflects the current, composite state of the Japes project. This repository also serves as the administrative hub for the project where organization-wide policies are performed. Many other repositories may be curated by this organization. Some important ones include:

- `japeslang/japes` - this repository; Includes administrative-level documentation, Japes Formal Specification, VMR repository.
- `japeslang/toolchain` - Japes compiler Pipeline (including formal grammar), Jinks build system, J4 macro processor (including formal grammar),   
- `japeslang/stdlib` - the Japes standard library implementation.

## Governance

Governance shall be described in greater detail in the future, and a code of conduct will be drafted. All people who make use of the Japes project are Users. Contributors are users who materially contribute to the the Japes project and not only include programmers, but also include technical specialists such as technical writers, translators, mathematicians, artists, and other domain experts. Maintainers are contributors who are capable of approving changes to a curated repository. Users may participate in the peer review of a pull request; contributors create them, and mantainers approve them. Until governance is decided, thylordroot is the provisional head of decision-making for this project. 

## Vibe Coding Prohibited

This project makes no comment on the general state of generative artificial intelligence (AI) and its metaphysical properties except to say that the proposition of whether machines can or cannot be intelligent is not testable in the present. It is absolutely imperative that all of the code produced by this project is (to the greatest extent possible) free from defect. Pull Request (PR) acceptance is conditional on your code being free from work products (i.e., code, specifications, or documentation) derived from AI. When applied to the context of writing software, this practice is sometimes known as "vibe coding". This practice should be avoided at all costs within the repositories in `japeslang`. It is not feasible to prevent AI from analyzing the code and offering pointers. It is this project's current position to do nothing to prevent that. It is possible that generative AI may make a useful screening tool in any event.

Regardless of its future capability, generative AI at the time of writing has a reputation for its readiness to hallucinate. That's to be expected from any machine model (to say nothing of one that shares attributes in common with biological neural networks). Legality may vary by jurisdiction, but precedent is relatively convincing that non-humans cannot originate copyright. Models may unwittingly include patents to which no contributor may grant a license to, and they may lift code from textbooks which are still very much copyrighted. 

Support for AI was once made available in a rudimentary and easily broken form, but the offer was always rescindable, and this recission has occurred. It may not be undone barring an Support for AI was once made available in a rudimentary and easily broken form, but the offer was always rescindable, and this recission has occurred. It may not be undone barring an RFC; as RFC1 has not even been written yet, there is no plan to officially support this in the future. Therefore, the rights afforded to you respecting AI are the set of the rights you have always had. These are the rights given by a work product's license, which is mostly GPLv3 + Classpath (but which in some cases may include CC_BY_ND4.0 or MIT).  The vibe-code moratorium remains, however: no PR will be accepted if there exists unresolved suspiscion or knowledge of it containing work products generated by AI.