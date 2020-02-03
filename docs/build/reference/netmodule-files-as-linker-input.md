---
title: .netmodule fichiers en tant qu’entrée dans l’éditeur de liens
description: Décrit comment utiliser mixed.obj les.netmodule fichiers en tant qu’entrée de l’éditeur de liens lors de la création d’assemblys .NET.
ms.date: 01/30/2020
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodule files
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
no-loc:
- obj
- netmodule
- clr
- pure
- safe
ms.openlocfilehash: 83eab25624bdb81ba9191e4efe6a774551502ee0
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912826"
---
# <a name="opno-locnetmodule-files-as-linker-input"></a>.netmodule fichiers en tant qu’entrée dans l’éditeur de liens

Link. exe accepte les fichiers MSIL *`.obj`* et *`.netmodule`* comme entrée. Le fichier de sortie produit par l’éditeur de liens est un assembly ou un fichier *`.netmodule`* sans dépendance au moment de l’exécution sur l’un des fichiers *`.obj`* ou *`.netmodule`* qui ont été entrés dans l’éditeur de liens.

## <a name="remarks"></a>Notes

*`.netmodule`* fichiers sont créés par le compilateur MSVC avec [/ln (créer un module MSIL)](ln-create-msil-module.md) ou par l’éditeur de liens avec [/noAssembly (créer un module MSIL)](noassembly-create-a-msil-module.md). les fichiers de *`.obj`* sont toujours créés C++ dans une compilation. Pour d’autres compilateurs Visual Studio, utilisez l’option de compilateur **/target:module**.

L’éditeur de liens doit recevoir le fichier *`.obj`* à partir C++ de la compilation qui a créé le *`.netmodule`* . Le passage d’un *`.netmodule`* n’est plus pris en charge, car les **/clr:pure** et **/clr:** les options du compilateursafesont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017 et versions ultérieures.

Pour plus d’informations sur l’appel de l’éditeur de liens à partir de la ligne de commande, consultez Syntaxe de la ligne de commande de l' [éditeur de liens](linking.md), [utilisation de l’ensemble d’outils MSVC à partir de la ligne de commande](../building-on-the-command-line.md)et [définition du chemin d’accès et des variables d’environnement pour les générations en ligne de commande](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Le passage d’un fichier *`.netmodule`* ou *`.dll`* à l’éditeur de liens qui a été compilé par le compilateur MSVC avec **/clr** peut provoquer une erreur de l’éditeur de liens. Pour plus d’informations, consultez [la page choix du format des fichiers d’entrée.netmodule ](choosing-the-format-of-netmodule-input-files.md).

L’éditeur de liens accepte à la fois les fichiers de *`.obj`* natif et les fichiers de *`.obj`* MSIL compilés avec **/clr** . Vous pouvez passer des fichiers de *`.obj`* mixtes dans la même Build. La vérifiabilité par défaut du fichier de sortie résultant est identique à la vérifiabilité du module d’entrée le plus bas.

Vous pouvez modifier une application composée de deux ou plusieurs assemblys qui doivent être contenus dans un assembly. Recompilez les sources des assemblys, puis liez les fichiers *`.obj`* ou les fichiers *`.netmodule`* pour produire un assembly unique.

Spécifiez un point d’entrée à l’aide [de/Entry (symbole de point d’entrée) lors de](entry-entry-point-symbol.md) la création d’une image exécutable.

Quand vous établissez un lien avec un fichier *`.obj`* ou *`.netmodule`* MSIL, utilisez [/LTCG (génération de code durant l’édition de liens)](ltcg-link-time-code-generation.md); sinon, lorsque l’éditeur de liens rencontre le *`.obj`* MSIL ou *`.netmodule`* , il redémarre le lien avec **/LTCG**. Vous verrez un message d’information indiquant que le lien est en redémarrant. Vous pouvez ignorer ce message, mais pour améliorer les performances de l’éditeur de liens, spécifiez explicitement **/LTCG**.

Les fichiers *`.obj`* ou *`.netmodule`* MSIL peuvent également être passés à cl. exe.

Les fichiers de *`.obj`* ou de *`.netmodule`* MSIL d’entrée ne peuvent pas avoir de ressources incorporées. Incorporez des ressources dans un module de sortie ou un fichier d’assembly à l’aide de l’option de l’éditeur de liens [/ASSEMBLYRESOURCE (incorporer une ressource managée)](assemblyresource-embed-a-managed-resource.md) . Vous pouvez également utiliser l’option du compilateur **/Resource** dans d’autres compilateurs Visual Studio.

## <a name="examples"></a>Exemples

Dans C++ le code, le bloc **`catch`** d’un **`try`** correspondant sera appelé pour une exception non`System`. Toutefois, par défaut, le CLR encapsule les exceptions non`System` avec <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Lorsqu’un assembly est créé C++ à partir deC++ et des modules non, et que vous souhaitez C++ qu’un bloc **`catch`** dans le code soit appelé à partir de sa clause **`try`** correspondante lorsque le bloc **`try`** lève une exception non`System`, vous devez ajouter l’attribut `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` au code source pourC++ les non-modules.

```cpp
// MSIL_linking.cpp
// compile with: /c /clr
value struct V {};

ref struct MCPP {
   static void Test() {
      try {
         throw (gcnew V);
      }
      catch (V ^) {
         System::Console::WriteLine("caught non System exception in C++ source code file");
      }
   }
};

/*
int main() {
   MCPP::Test();
}
*/
```

En modifiant la valeur `Boolean` de l’attribut `WrapNonExceptionThrows`, vous modifiez la capacité du C++ code à intercepter une exception non`System`.

```csharp
// MSIL_linking_2.cs
// compile with: /target:module /addmodule:MSIL_linking.obj
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console
using System.Runtime.CompilerServices;

// enable non System exceptions
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]

class MLinkTest {
   public static void Main() {
      try {
         MCPP.Test();
      }
      catch (RuntimeWrappedException) {
         System.Console.WriteLine("caught a wrapped exception in C#");
      }
   }
}
```

```Output
caught non System exception in C++ source code file
```

## <a name="see-also"></a>Voir aussi

- [Fichiers d’entrée LINK](link-input-files.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
