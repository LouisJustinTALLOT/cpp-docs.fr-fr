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

Si vous choisissez d’utiliser **__declspec (dllimport)** ainsi qu’un fichier .def, vous devez modifier le fichier .def pour utiliser des données à la place de constante pour réduire la probabilité que le codage incorrect entraîne un problème :

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

Le tableau suivant montre pourquoi.

|Mot clé|Émet dans la bibliothèque d’importation|Exportations|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

À l’aide de **__declspec (dllimport)** et constante répertorie les deux le `imp` version et le nom non décoré dans la DLL .lib importer la bibliothèque qui est créée pour permettre la liaison explicite. À l’aide de **__declspec (dllimport)** et des listes de données uniquement le `imp` version du nom.

Si vous utilisez (constante), les constructions de code suivantes peuvent être utilisées pour accéder à `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\- ou -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Toutefois, si vous utilisez des données dans votre fichier .def, seul le code compilé avec la définition suivante peut accéder à la variable `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

À l’aide de la constante est plus risqué, car si vous oubliez d’utiliser le niveau supplémentaire d’indirection, vous pourriez éventuellement accéder un pointeur de la table adresses d’importation à la variable, pas la variable elle-même. Ce type de problème peut se manifester souvent une violation d’accès, car la table d’importation adresse est actuellement en lecture seule par le compilateur et l’éditeur de liens.

L’éditeur de liens MSVC actuel émet un avertissement s’il voit constante dans le fichier .def pour prendre en compte pour ce cas. La seule véritable raison d’utiliser constante est que si vous ne pouvez pas recompiler un fichier objet quelconque dans lequel le fichier d’en-tête ne pas répertorier **__declspec (dllimport)** sur le prototype.

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
