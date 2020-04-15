---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 9ede0d3b53c975298dea3d1331bc0fb00ac246b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328256"
---
# <a name="exports"></a>EXPORTS

Introduit une section d'une ou plusieurs définitions d'exportation qui spécifient les ordinaux ou noms exportés des fonctions ou données. Chaque définition doit être sur une ligne distincte.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Notes

La première *définition* peut être sur `EXPORTS` la même ligne que le mot clé ou sur une ligne ultérieure. Le fichier .DEF peut contenir une ou plusieurs instructions `EXPORTS`.

La syntaxe pour une *définition* d’exportation est la suivante :

> *nom d’entrée*\[__=__*internal_name*|*other_module.exported_name*] \[ **\@** _ordinal_ \[ **NONAME**] ] \[ \[ **PRIVATE**] \[ **DONNÉES**] ]

*nom d’entrée* est la fonction ou le nom variable que vous voulez exporter. Cela est nécessaire. Si le nom que vous exportez diffère du nom de la DLL, spécifiez le nom de l’exportation dans la DLL en utilisant *internal_name*. Par exemple, si votre DLL exporte une fonction `func1` et que vous voulez que les appelants l'utilisent comme `func2`, vous devez spécifier :

```DEF
EXPORTS
   func2=func1
```

Si le nom que vous exportez provient d’un autre module, spécifiez le nom de l’exportation dans le DLL en utilisant *other_module.exported_name*. Par exemple, si votre DLL exporte une fonction `other_module.func1` et que vous voulez que les appelants l'utilisent comme `func2`, vous devez spécifier :

```DEF
EXPORTS
   func2=other_module.func1
```

Si le nom que vous exportez provient d’un autre module qui exporte par ordinaire, spécifiez l’ordinaire de l’exportation dans la DLL en utilisant *other_module*. __#__ *ordinal*. Par exemple, si votre DLL exporte une fonction à partir de l’autre module où `func2`il est ordinaire 42, et que vous voulez que les appelants l’utilisent comme , vous pouvez spécifier:

```DEF
EXPORTS
   func2=other_module.#42
```

Étant donné que le compilateur MSVC utilise la décoration de nom *internal_name* pour les fonctions de C, `extern "C"` vous devez soit utiliser le nom décoré internal_name ou définir les fonctions exportées en utilisant dans le code source. Le compilateur décore également les fonctions C qui utilisent la convention [d’appel __stdcall](../../cpp/stdcall.md) avec un préfixe de souligner (\_) et un suffixe composé du signe à l’heure ()\@suivi par le nombre d’octets (en décimale) dans la liste d’argumentation.

Pour trouver les noms décorés produits par le compilateur, utilisez l’outil [DUMPBIN](dumpbin-reference.md) ou l’option [linker/MAP.](map-generate-mapfile.md) Les noms décorés sont spécifiques au compilateur. Si vous exportez les noms décorés dans le fichier .DEF, les exécutables qui sont liés à la DLL doivent également être générés à l'aide la même version du compilateur. Cela garantit que les noms décorés dans l'appelant correspondent aux noms exportés dans le fichier .DEF.

Vous pouvez \@utiliser *l’ordinaire* pour spécifier qu’un numéro, et non le nom de la fonction, entre dans la table d’exportation de la DLL. De nombreuses DLL Windows exportent des ordinaux pour prendre en charge du code hérité. Il était courant d'utiliser des ordinaux dans le code Windows 16 bits, car cela peut aider à réduire la taille d'une DLL. Nous ne recommandons pas d’exporter des fonctions par ordinaire à moins que les clients de votre DLL en ont besoin pour le soutien de l’héritage. Comme le fichier .LIB contiendra le mappage entre l'ordinal et la fonction, vous pouvez utiliser le nom de fonction comme vous le feriez normalement dans les projets qui utilisent la DLL.

En utilisant le mot-clé **NONAME** en option, vous pouvez exporter par ordinaire seulement et réduire la taille de la table d’exportation dans le DLL résultant. Toutefois, si vous voulez utiliser [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) sur le DLL, vous devez connaître l’ordinaire parce que le nom ne sera pas valide.

Le mot clé en option **PRIVATE** empêche *le nom d’entrée* d’être inclus dans la bibliothèque d’importation générée par LINK. Il n'affecte pas l'exportation dans l'image également générée par LINK.

Le mot clé en option **DATA** spécifie qu’une exportation est une donnée, et non un code. Cet exemple illustre comment vous pouvez exporter une variable de données nommée `exported_global` :

```DEF
EXPORTS
   exported_global DATA
```

Il existe quatre méthodes pour exporter une définition, répertoriées dans l'ordre recommandé :

1. Le mot clé [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source

1. Une instruction `EXPORTS` dans un fichier .DEF

1. Spécifications [/EXPORT](export-exports-a-function.md) dans une commande LINK

1. Une directive [de commentaire](../../preprocessor/comment-c-cpp.md) dans le `#pragma comment(linker, "/export: definition ")`code source, du formulaire . L’exemple suivant montre une directive de commentaire `PlainFuncName` #pragma avant une déclaration de `_PlainFuncName@4` fonction, où se trouve le nom non décoré, et est le nom décoré de la fonction :

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

La directive #pragma est utile si vous avez besoin d’exporter un nom de fonction non décontré, et avez des exportations différentes en fonction de la configuration de construction (par exemple, dans les constructions 32 ou 64 bits).

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
