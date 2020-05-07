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
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273415"
---
# <a name="importing-using-def-files"></a>Importation à l'aide de fichiers DEF

Si vous choisissez d’utiliser **__declspec (dllimport)** avec un fichier. def, vous devez modifier le fichier. def pour utiliser les données à la place de constant afin de réduire la probabilité qu’un code incorrect provoque un problème :

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

L’utilisation de **__declspec (dllimport)** et de la `imp` constante répertorie à la fois la version et le nom non décoré dans la bibliothèque d’importation de dll. lib qui est créée pour autoriser la liaison explicite. L’utilisation de **__declspec (dllimport)** et des données `imp` répertorie uniquement la version du nom.

Si vous utilisez CONSTANT, l’une des constructions de code suivantes peut être utilisée pour accéder `ulDataInDll`à :

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\- ou -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Toutefois, si vous utilisez des données dans votre fichier. def, seul le code compilé avec la définition suivante peut accéder `ulDataInDll`à la variable :

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

L’utilisation de CONSTANT est plus risquée, car si vous oubliez d’utiliser le niveau supplémentaire d’indirection, vous pouvez accéder au pointeur de la table d’adresses d’importation vers la variable, et non à la variable elle-même. Ce type de problème peut souvent se manifester comme une violation d’accès, car la table d’adresses d’importation est actuellement mise en lecture seule par le compilateur et l’éditeur de liens.

L’éditeur de liens MSVC actuel émet un avertissement s’il voit une constante dans le fichier. def pour tenir compte de ce cas. La seule véritable raison d’utiliser CONSTANT est si vous ne pouvez pas recompiler un fichier objet dans lequel le fichier d’en-tête ne faisait pas partie de la liste **__declspec (dllimport)** sur le prototype.

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
