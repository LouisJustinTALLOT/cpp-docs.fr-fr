---
title: Fichiers .netmodule en tant qu'entrée de l'Éditeur de liens
ms.date: 05/16/2019
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: 50a0f0a1ff5f65a7512e8372de2fe5296c866dca
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837427"
---
# <a name="netmodule-files-as-linker-input"></a>Fichiers .netmodule en tant qu'entrée de l'Éditeur de liens

link.exe accepte désormais les fichiers MSIL .obj et .netmodule en entrée. Le fichier de sortie produit par l’éditeur de liens est un assembly ou un fichier .netmodule qui ne dépend pas au moment de l’exécution des fichiers .obj ou .netmodule fournis en entrée à l’éditeur de liens.

Les fichiers .netmodule sont créés par le compilateur MSVC avec [/LN (Créer le module MSIL)](ln-create-msil-module.md) ou par l’éditeur de liens avec [/NOASSEMBLY (Créer un module MSIL)](noassembly-create-a-msil-module.md). Les fichiers .obj sont toujours créés dans une compilation Visual C++. Pour d’autres compilateurs Visual Studio, utilisez l’option de compilateur **/target:module**.

Vous devez passer à l’éditeur de liens le fichier .obj provenant de la compilation Visual C++ ayant créé le fichier .netmodule. Le passage d’un fichier .netmodule n’est plus pris en charge car les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017 et ultérieur.

Pour plus d’informations sur la façon d’appeler l’éditeur de liens à partir de la ligne de commande, consultez [Syntaxe de la ligne de commande de l’éditeur de liens](linking.md), [Utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](../building-on-the-command-line.md) et [Définir les variables de chemin et d’environnement pour les builds générées à partir de la ligne de commande](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Le passage d’un fichier .netmodule ou .dll à l’éditeur de liens compilé par le compilateur MSVC avec **/clr** peut entraîner une erreur de l’éditeur de liens. Pour plus d’informations, consultez [Choix du format des fichiers d’entrée .netmodule](choosing-the-format-of-netmodule-input-files.md).

L’éditeur de liens accepte les fichiers .obj natifs ainsi que les fichiers MSIL .obj compilés avec **/clr**. Lors du passage de fichiers .obj mixtes dans la même build, la vérifiabilité du fichier de sortie obtenu est par défaut égale au niveau de vérifiabilité le plus bas des modules d’entrée.

Si vous avez actuellement une application composée d’au moins deux assemblys et que vous souhaitez la faire tenir dans un seul assembly, vous devez recompiler les assemblys, puis lier les fichiers .obj ou .netmodule pour produire un seul assembly.

Vous devez spécifier un point d’entrée avec [/ENTRY (Symbole de point d’entrée)](entry-entry-point-symbol.md) lors de la création d’une image exécutable.

En cas de lien avec un fichier MSIL .obj ou .netmodule, utilisez [/LTCG (Génération de code durant l’édition de liens)](ltcg-link-time-code-generation.md) ; sinon, quand l’éditeur de liens rencontre le fichier MSIL .obj ou .netmodule, il redémarre le lien avec /LTCG.

Vous pouvez également passer les fichiers MSIL .obj ou .netmodule à cl.exe.

Les fichiers MSIL .obj ou .netmodule en entrée ne peuvent pas avoir de ressources incorporées. Une ressource est incorporée dans un fichier de sortie (module ou assembly) avec l’option d’éditeur de liens [/ASSEMBLYRESOURCE (Incorporer une ressource managée)](assemblyresource-embed-a-managed-resource.md) ou avec l’option de compilateur **/resource** dans d’autres compilateurs Visual Studio.

Si vous ne spécifiez pas [/LTCG (Génération de code durant l’édition de liens)](ltcg-link-time-code-generation.md) lors de l’établissement d’un lien MSIL, un message informatif indiquant que le lien est en cours de redémarrage s’affiche. Vous pouvez ignorer ce message ; toutefois, pour améliorer les performances de l’éditeur de liens avec le lien MSIL, spécifiez explicitement **/LTCG**.

## <a name="example"></a>Exemple

Dans le code C++, le bloc **catch** d’une clause **try** correspondante est appelé pour une exception non-système. Cependant, par défaut, le CLR wrappe les exceptions non-système avec <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Lorsqu’un assembly est créé à partir de modules Visual C++ et non-Visual C++ et que vous souhaitez qu’un bloc **catch** dans du code C++ soit appelé à partir de sa clause **try** correspondante quand le bloc **try** lève une exception non-système, vous devez ajouter l’attribut `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` au code source des modules non-C++.

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

## <a name="example"></a>Exemple

En changeant la valeur booléenne de l’attribut `WrapNonExceptionThrows`, vous modifiez la capacité du code Visual C++ à intercepter une exception non-système.

```cpp
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
