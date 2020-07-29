---
title: Fonctions d'importation et d'exportation de DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
ms.openlocfilehash: 753a51fa8e2c87b77a54e5e93522e5f11585b610
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200073"
---
# <a name="dll-import-and-export-functions"></a>Fonctions d'importation et d'exportation de DLL

**Spécifique à Microsoft**

Les informations les plus complètes et récentes à ce sujet se trouvent dans la rubrique [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Les **`dllimport`** `dllexport` modificateurs de classe de stockage et sont des extensions spécifiques à Microsoft pour le langage C. Ces modificateurs définissent explicitement l'interface de la DLL à son client (le fichier exécutable ou une autre DLL). La déclaration de fonctions comme `dllexport` élimine le besoin d'utiliser un fichier de définition de module (.DEF). Vous pouvez également utiliser les **`dllimport`** `dllexport` modificateurs et avec des données et des objets.

Les **`dllimport`** `dllexport` modificateurs de classe de stockage et doivent être utilisés avec le mot clé de syntaxe d’attribut étendu, **`__declspec`** , comme indiqué dans cet exemple :

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllExport int j;
DllExport int n;
```

Pour obtenir des informations spécifiques sur la syntaxe des modificateurs étendus de classe de stockage, consultez [Attributs étendus de classe de stockage](../c-language/c-extended-storage-class-attributes.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Définitions de fonction C](../c-language/c-function-definitions.md)
