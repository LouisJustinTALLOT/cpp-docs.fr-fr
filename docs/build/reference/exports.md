---
title: EXPORTATIONS | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bf350b0a129c642678fc6af1bac7d35633fe909
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860977"
---
# <a name="exports"></a>EXPORTS

Introduit une section d'une ou plusieurs définitions d'exportation qui spécifient les ordinaux ou noms exportés des fonctions ou données. Chaque définition doit être sur une ligne distincte.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Notes

La première *définition* peut se trouver sur la même ligne que le `EXPORTS` mot clé ou sur une ligne suivante. Le fichier .DEF peut contenir une ou plusieurs instructions `EXPORTS`.

La syntaxe pour une exportation *définition* est :

> *nom d’entrée*\[__=__*internal_name*|*other_module.exported_name*] \[ **\@** _ordinale_ \[ **NONAME**]] \[ \[ **privé**] | \[ **Données**]]

*nom d’entrée* est le nom de fonction ou une variable que vous souhaitez exporter. Cet élément est obligatoire. Si le nom que vous exportez diffère du nom dans la DLL, spécifiez nom de l’exportation dans la DLL à l’aide de *internal_name*. Par exemple, si votre DLL exporte une fonction `func1` et que vous voulez que les appelants l'utilisent comme `func2`, vous devez spécifier :

```DEF
EXPORTS
   func2=func1
```

Si le nom que vous exportez provient d’un autre module, spécifiez nom de l’exportation dans la DLL à l’aide de *other_module.exported_name*. Par exemple, si votre DLL exporte une fonction `other_module.func1` et que vous voulez que les appelants l'utilisent comme `func2`, vous devez spécifier :

```DEF
EXPORTS
   func2=other_module.func1
```

Si le nom que vous exportez à partir d’un autre module qui exporte par ordinal, spécifiez l’exportation de la position ordinale dans la DLL à l’aide *other_module*.__#__ *ordinale*. Par exemple, si votre DLL exporte une fonction à partir du module où il est 42 ordinale, et que vous souhaitez les appelants à utiliser en tant que `func2`, vous devez spécifier :

```DEF
EXPORTS
   func2=other_module.#42
```

Étant donné que le compilateur Visual C++ utilise la décoration de nom pour les fonctions C++, vous devez utiliser le nom décoré *internal_name* ou définir les fonctions exportées à l’aide de `extern "C"` dans le code source. Le compilateur décore également les fonctions C qui utilisent le [__stdcall](../../cpp/stdcall.md) convention avec un trait de soulignement d’appel (\_) préfixe et un suffixe composé de l’arobase (\@) suivi du nombre d’octets (au format décimal) dans le liste d’arguments.

Pour rechercher les noms décorés produits par le compilateur, utilisez le [DUMPBIN](../../build/reference/dumpbin-reference.md) outil ou l’éditeur de liens [/mapper](../../build/reference/map-generate-mapfile.md) option. Les noms décorés sont spécifiques au compilateur. Si vous exportez les noms décorés dans le fichier .DEF, les exécutables qui sont liés à la DLL doivent également être générés à l'aide la même version du compilateur. Cela garantit que les noms décorés dans l'appelant correspondent aux noms exportés dans le fichier .DEF.

Vous pouvez utiliser \@ *ordinale* pour spécifier qu’un nombre et non le nom de fonction, passe dans la table d’exportation de la DLL. De nombreuses DLL Windows exportent des ordinaux pour prendre en charge du code hérité. Il était courant d'utiliser des ordinaux dans le code Windows 16 bits, car cela peut aider à réduire la taille d'une DLL. Nous ne conseillons pas l'exportation de fonctions par ordinal à moins que vos clients de DLL en aient besoin pour une prise en charge héritée. Comme le fichier .LIB contiendra le mappage entre l'ordinal et la fonction, vous pouvez utiliser le nom de fonction comme vous le feriez normalement dans les projets qui utilisent la DLL.

À l’aide de l’élément facultatif **NONAME** mot clé, vous pouvez exporter par ordinal uniquement et réduire la taille de la table d’exportation dans la DLL résultante. Toutefois, si vous souhaitez utiliser [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) sur la DLL, vous devez connaître l’ordinal, car le nom ne sera pas valid.

Le mot clé facultatif **privé** empêche *nom d’entrée* d’être inclus dans la bibliothèque d’importation générée par LINK. Il n'affecte pas l'exportation dans l'image également générée par LINK.

Le mot clé facultatif **données** Spécifie qu’une exportation donnée, et non le code. Cet exemple illustre comment vous pouvez exporter une variable de données nommée `exported_global` :

```DEF
EXPORTS
   exported_global DATA
```

Il existe quatre méthodes pour exporter une définition, répertoriées dans l'ordre recommandé :

1. Le [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) mot clé dans le code source

1. Une instruction `EXPORTS` dans un fichier .DEF

1. Un [/EXPORT](../../build/reference/export-exports-a-function.md) spécification dans une commande LINK

1. Un [commentaire](../../preprocessor/comment-c-cpp.md) directive dans le code source, sous la forme `#pragma comment(linker, "/export: definition ")`. L’exemple suivant montre une directive de commentaire de #pragma avant une déclaration de fonction, où `PlainFuncName` est le nom non décoré, et `_PlainFuncName@4` est le nom décoré de la fonction :

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

La directive #pragma est utile si vous devez exporter le nom d’une fonction non décoré et avez exportations différents en fonction de la configuration de build (par exemple, dans les versions 32 bits ou 64 bits).

Ces quatre méthodes peuvent être utilisées dans le même programme. Quand LINK génère un programme qui contient des exportations, il crée également une bibliothèque d'importation, à moins qu'un fichier .EXP soit utilisé dans la build.

Voici un exemple de section EXPORTS :

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

Quand vous exportez une variable à partir d'une DLL en utilisant un fichier .DEF, vous n'êtes pas tenu de spécifier `__declspec(dllexport)` sur la variable. Toutefois, dans tout fichier qui utilise la DLL, vous devez encore utiliser `__declspec(dllimport)` sur la déclaration des données.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)
