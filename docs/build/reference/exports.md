---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 8338f27d35d3779a55b83b70c7a3eef285a91f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492884"
---
# <a name="exports"></a>EXPORTS

Introduit une section d'une ou plusieurs définitions d'exportation qui spécifient les ordinaux ou noms exportés des fonctions ou données. Chaque définition doit être sur une ligne distincte.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Notes

La première *définition* peut être sur la même ligne que le `EXPORTS` mot clé ou sur une ligne suivante. Le fichier .DEF peut contenir une ou plusieurs instructions `EXPORTS`.

La syntaxe d’une *définition* d’exportation est la suivante:

> *entryname* *internal_name other_module. exported_name*] ordinal\[ **NoName]** ] \[ **\@** |\[ __=__ \[ \[ **Privé**] | **Données]** ] \[

*entryname* est le nom de la fonction ou de la variable que vous souhaitez exporter. Cet élément est obligatoire. Si le nom que vous exportez est différent du nom de la DLL, spécifiez le nom de l’exportation dans la DLL à l’aide de *internal_name*. Par exemple, si votre DLL exporte une fonction `func1` et que vous voulez que les appelants l'utilisent comme `func2`, vous devez spécifier :

```DEF
EXPORTS
   func2=func1
```

Si le nom que vous exportez provient d’un autre module, spécifiez le nom de l’exportation dans la DLL à l’aide de *other_module. exported_name*. Par exemple, si votre DLL exporte une fonction `other_module.func1` et que vous voulez que les appelants l'utilisent comme `func2`, vous devez spécifier :

```DEF
EXPORTS
   func2=other_module.func1
```

Si le nom que vous exportez provient d’un autre module qui exporte par ordinal, spécifiez l’ordinal de l’exportation dans la DLL à l’aide de *other_module*. __#__ *ordinal*. Par exemple, si votre dll exporte une fonction à partir de l’autre module où elle est ordinale 42 et que vous souhaitez que les `func2`appelants l’utilisent en tant que, vous devez spécifier:

```DEF
EXPORTS
   func2=other_module.#42
```

Étant donné que le compilateur MSVC utilise la C++ décoration de noms pour les fonctions, vous devez utiliser le nom décoré *internal_name* ou définir les `extern "C"` fonctions exportées à l’aide de dans le code source. Le compilateur décore également les fonctions C qui utilisent la Convention d’appel [_ _ stdcall](../../cpp/stdcall.md) avec\_un préfixe de trait de soulignement ()\@et un suffixe composé du signe arobase () suivi du nombre d’octets (au format décimal) dans la liste d’arguments.

Pour rechercher les noms décorés produits par le compilateur, utilisez l’outil [DUMPBIN](dumpbin-reference.md) ou l’option [/Map](map-generate-mapfile.md) de l’éditeur de liens. Les noms décorés sont spécifiques au compilateur. Si vous exportez les noms décorés dans le fichier .DEF, les exécutables qui sont liés à la DLL doivent également être générés à l'aide la même version du compilateur. Cela garantit que les noms décorés dans l'appelant correspondent aux noms exportés dans le fichier .DEF.

Vous pouvez utiliser \@ *ordinal* pour spécifier qu’un nombre, et non le nom de la fonction, est placé dans la table d’exportation de la dll. De nombreuses DLL Windows exportent des ordinaux pour prendre en charge du code hérité. Il était courant d'utiliser des ordinaux dans le code Windows 16 bits, car cela peut aider à réduire la taille d'une DLL. Nous ne conseillons pas l'exportation de fonctions par ordinal à moins que vos clients de DLL en aient besoin pour une prise en charge héritée. Comme le fichier .LIB contiendra le mappage entre l'ordinal et la fonction, vous pouvez utiliser le nom de fonction comme vous le feriez normalement dans les projets qui utilisent la DLL.

En utilisant le mot clé facultatif **NoName** , vous pouvez exporter par ordinal uniquement et réduire la taille de la table d’exportation dans la DLL résultante. Toutefois, si vous souhaitez utiliser [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) sur la dll, vous devez connaître l’ordinal, car le nom n’est pas valide.

Le mot clé facultatif **Private** empêche l’inclusion de *entryname* dans la bibliothèque d’importation générée par Link. Il n'affecte pas l'exportation dans l'image également générée par LINK.

Les **données** de mot clé facultatives spécifient qu’une exportation est des données et non du code. Cet exemple illustre comment vous pouvez exporter une variable de données nommée `exported_global` :

```DEF
EXPORTS
   exported_global DATA
```

Il existe quatre méthodes pour exporter une définition, répertoriées dans l'ordre recommandé :

1. Mot clé [_ _ declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source

1. Une instruction `EXPORTS` dans un fichier .DEF

1. Une spécification [/Export](export-exports-a-function.md) dans une commande Link

1. Directive de [Commentaire](../../preprocessor/comment-c-cpp.md) dans le code source, sous la forme `#pragma comment(linker, "/export: definition ")`. L’exemple suivant montre un #pragma directive de commentaire avant une déclaration de fonction `PlainFuncName` , où est le nom non décoré `_PlainFuncName@4` et est le nom décoré de la fonction:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

La directive #pragma est utile si vous devez exporter un nom de fonction non décoré et avoir des exportations différentes en fonction de la configuration de build (par exemple, dans les builds 32 bits ou 64 bits).

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

[Règles s’appliquant aux instructions de définition de module](rules-for-module-definition-statements.md)
