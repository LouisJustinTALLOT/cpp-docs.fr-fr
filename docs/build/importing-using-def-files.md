---
title: Importation à l'aide de fichiers DEF
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: e4ac48dc013874c240411f78a733d32e116df25d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223965"
---
# <a name="importing-using-def-files"></a>Importation à l'aide de fichiers DEF

Si vous choisissez d’utiliser **`__declspec(dllimport)`** avec un fichier. def, vous devez modifier le fichier. def pour utiliser les données à la place de constant afin de réduire la probabilité qu’un code incorrect provoque un problème :

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

Le tableau suivant indique pourquoi.

|Mot clé|Émissions dans la bibliothèque d’importation|Exports|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

L’utilisation de **`__declspec(dllimport)`** et de constantes répertorie la `imp` version et le nom non décoré dans la bibliothèque d’importation de dll. lib qui est créée pour autoriser la liaison explicite. L’utilisation **`__declspec(dllimport)`** de et des données répertorie uniquement la `imp` version du nom.

Si vous utilisez CONSTANT, l’une des constructions de code suivantes peut être utilisée pour accéder à `ulDataInDll` :

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\- ou -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Toutefois, si vous utilisez des données dans votre fichier. def, seul le code compilé avec la définition suivante peut accéder à la variable `ulDataInDll` :

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

L’utilisation de CONSTANT est plus risquée, car si vous oubliez d’utiliser le niveau supplémentaire d’indirection, vous pouvez accéder au pointeur de la table d’adresses d’importation vers la variable, et non à la variable elle-même. Ce type de problème peut souvent se manifester comme une violation d’accès, car la table d’adresses d’importation est actuellement mise en lecture seule par le compilateur et l’éditeur de liens.

L’éditeur de liens MSVC actuel émet un avertissement s’il voit une constante dans le fichier. def pour tenir compte de ce cas. La seule raison réelle d’utiliser une constante est si vous ne pouvez pas recompiler un fichier objet dans lequel le fichier d’en-tête n’a pas été répertorié **`__declspec(dllimport)`** sur le prototype.

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
