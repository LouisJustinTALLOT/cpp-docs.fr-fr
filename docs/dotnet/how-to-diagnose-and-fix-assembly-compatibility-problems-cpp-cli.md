---
title: 'Comment : diagnostiquer et résoudre les problèmes de compatibilité d’Assembly (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4440ab455aff8922c108cdb35cff041cd67f56d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133418"
---
# <a name="how-to-diagnose-and-fix-assembly-compatibility-problems-ccli"></a>Comment : diagnostiquer et résoudre les problèmes de compatibilité de l'assembly (C++/CLI)
Cette rubrique explique ce qui peut se produire lorsque la version d’un assembly référencé au moment de la compilation ne correspond pas à la version de l’assembly référencé lors de l’exécution et comment éviter le problème.  
  
 Lorsqu’un assembly est compilé, les autres assemblys peuvent être référencés avec la `#using` syntaxe. Lors de la compilation, ces assemblys sont accessibles par le compilateur. Informations à partir de ces assemblys sont utilisées pour prendre des décisions d’optimisation.  
  
 Toutefois, si l’assembly référencé est modifié et recompilé, et vous ne recompilez pas l’assembly de référence est dépendant, les assemblys peut ne pas toujours être compatibles. Les décisions d’optimisation qui étaient valides au premier peut-être pas correctes par rapport à la nouvelle version de l’assembly. Diverses erreurs d’exécution peuvent se produire en raison de ces incompatibilités. Il n’existe aucune exception spécifique qui est produite dans ce cas. La façon de que l’échec est consigné lors de l’exécution dépend de la nature de la modification du code qui a provoqué le problème.  
  
 Ces erreurs ne doivent pas être un problème dans votre code de production final tant que l’application entière est reconstruite pour la version finale de votre produit. Les assemblys qui sont rendus accessibles au public doivent être marqués avec un numéro de version officielle, afin de vous assurer que ces problèmes sont évités. Pour plus d’informations, consultez [Versioning des assemblys](/dotnet/framework/app-domains/assembly-versioning).  
  
### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnostiquer et résoudre une erreur d’incompatibilité  
  
1.  Si vous rencontrez des exceptions d’exécution ou d’autres conditions d’erreur qui se produisent dans le code qui fait référence à un autre assembly et que vous avez aucun autre cause identifiée, vous pouvez être confronté à un assembly obsolète.  
  
2.  Tout d’abord, isoler et reproduire l’exception ou une autre condition d’erreur. Un problème qui se produit en raison d’une exception obsolète doit être reproductible.  
  
3.  Vérifiez l’horodatage de tous les assemblys référencés dans votre application.  
  
4.  Si les horodatages de tous les assemblys référencés sont ultérieures à l’horodatage de la dernière compilation de votre application, votre application est obsolète. Si cela se produit, recompiler votre application avec l’assembly le plus récent et apportez les modifications de code nécessaires.  
  
5.  Réexécutez l’application, effectuez les étapes pour reproduire le problème, vérifiez que l’exception ne se produit pas.  
  
## <a name="example"></a>Exemple  
 Le programme suivant illustre le problème en réduisant l’accessibilité d’une méthode et essayez d’accéder à cette méthode dans un autre assembly sans avoir à recompiler. Essayez de compiler `changeaccess.cpp` première. Il s’agit de l’assembly référencé, ce qui modifie. Ensuite, compilez `referencing.cpp`. La compilation réussit. Maintenant, réduisez l’accessibilité de la méthode appelée. Recompilez `changeaccess.cpp` avec l’indicateur `/DCHANGE_ACCESS`. Cela rend la méthode protégée, plutôt que privée, il peut donc plus être appelée légalement. Sans avoir à recompiler `referencing.exe`, réexécutez l’application. Une exception <xref:System.MethodAccessException> génère.  
  
```  
// changeaccess.cpp  
// compile with: /clr:safe /LD  
// After the initial compilation, add /DCHANGE_ACCESS and rerun  
// referencing.exe to introduce an error at runtime. To correct  
// the problem, recompile referencing.exe  
  
public ref class Test {  
#if defined(CHANGE_ACCESS)  
protected:  
#else  
public:  
#endif  
  
  int access_me() {  
    return 0;  
  }  
  
};  
  
```  
  
```  
// referencing.cpp  
// compile with: /clr:safe   
#using <changeaccess.dll>  
  
// Force the function to be inline, to override the compiler's own  
// algorithm.  
__forceinline  
int CallMethod(Test^ t) {  
  // The call is allowed only if access_me is declared public  
  return t->access_me();  
}  
  
int main() {  
  Test^ t = gcnew Test();  
  try  
  {  
    CallMethod(t);  
    System::Console::WriteLine("No exception.");  
  }  
  catch (System::Exception ^ e)  
  {  
    System::Console::WriteLine("Exception!");  
  }  
  return 0;  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [#using, Directive](../preprocessor/hash-using-directive-cpp.md)   
 [Types managés (C++-CLI)](../dotnet/managed-types-cpp-cli.md)