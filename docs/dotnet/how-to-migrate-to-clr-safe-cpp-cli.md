---
title: 'Comment : migrer vers - clr : safe (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- migration [C++], verifiable assemblies
- upgrading Visual C++ applications, verifiable assemblies
- verifiable assemblies [C++], migrating to
- /clr compiler option [C++], migrating to /clr:safe
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d72be19eb893a74a17a988e8c14c6bdaba766cbc
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704512"
---
# <a name="how-to-migrate-to-clrsafe-ccli"></a>Comment : effectuer une migration vers /clr:safe (C++/CLI)

> [!IMPORTANT]
> Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Si vous avez besoin des assemblys CLR safe, nous vous recommandons de que vous porter votre code en c#.

Si vous utilisez une version antérieure de la d’outils du compilateur Visual C++ à partir d’avant Visual Studio 2017, vous pouvez générer des composants vérifiables à l’aide de **/CLR : safe**, ce qui entraîne le compilateur à générer des erreurs pour chaque non vérifiable construction de code.

## <a name="remarks"></a>Notes

Les problèmes suivants génèrent des erreurs de vérifiabilité :

- Types natifs. Même s’il n’est pas utilisé, la déclaration de classes natives, des structures, des pointeurs ou des tableaux empêchera la compilation.

- Variables globales

- Appels de fonction dans toute bibliothèque non managée, y compris les appels de fonction common language runtime

- Une fonction vérifiable ne peut pas contenir un [opérateur static_cast](../cpp/static-cast-operator.md) pour la conversion vers le bas. Le [opérateur static_cast](../cpp/static-cast-operator.md) peut être utilisé pour effectuer un cast entre des types primitifs, mais pour downcast, [safe_cast](../windows/safe-cast-cpp-component-extensions.md) ou un cast de Style C (qui est implémenté comme un [safe_cast](../windows/safe-cast-cpp-component-extensions.md)) doit être utilisé.

- Une fonction vérifiable ne peut pas contenir un [reinterpret_cast, opérateur](../cpp/reinterpret-cast-operator.md) (ou tout cast de style C).

- Une fonction vérifiable ne peut pas effectuer une opération arithmétique sur une [interior_ptr (C + c++ / CLI)](../windows/interior-ptr-cpp-cli.md). Il peut uniquement lui affecter et déréférencer.

- Une fonction vérifiable peut uniquement lever ou intercepter des pointeurs vers des types référence pour les types de valeur doivent être convertie (boxed) avant de lever.

- Une fonction vérifiable peut uniquement appeler des fonctions vérifiables (telles que les appels au common language runtime ne sont pas autorisées, inclure `AtEntry` / `AtExit`, et par conséquent, les constructeurs globaux ne sont pas autorisées).

- Une classe vérifiable ne peut pas utiliser <xref:System.Runtime.InteropServices.LayoutKind>.

- Si vous générez un fichier EXE, d’une fonction principale ne peut pas déclarer de paramètres, par conséquent, <xref:System.Environment.GetCommandLineArgs%2A> doit être utilisé pour récupérer les arguments de ligne de commande.

- Effectue un appel non virtuel à une fonction virtuelle. Exemple :

   ```cpp
   // not_verifiable.cpp
   // compile with: /clr
   ref struct A {
      virtual void Test() {}
   };

   ref struct B : A {};

   int main() {
      B^ b1 = gcnew B;
      b1->A::Test();   // Non-virtual call to virtual function
   }
   ```

En outre, les mots clés suivants ne peut pas être utilisés dans du code vérifiable :

- [non managé](../preprocessor/managed-unmanaged.md) et [pack](../preprocessor/pack.md) pragmas

- [naked](../cpp/naked-cpp.md) et [aligner](../cpp/align-cpp.md) [__declspec](../cpp/declspec.md) modificateurs

- [__asm](../assembler/inline/asm.md)

- [__based](../cpp/based-grammar.md)

- [__try](../cpp/try-except-statement.md) et `__except`

## <a name="see-also"></a>Voir aussi

- [Code pur et vérifiable (C++-CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
