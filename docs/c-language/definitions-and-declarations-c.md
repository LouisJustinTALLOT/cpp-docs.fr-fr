---
title: Définitions et declarations (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d44a98fee82e41252b27fa5a1605b04a15af9115
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383483"
---
# <a name="definitions-and-declarations-c"></a>Définitions et déclarations (C)
**Section spécifique à Microsoft**  
  
 L'interface DLL fait référence à tous les éléments (fonctions et données) qui sont connus pour être exportés par un programme du système, c'est-à-dire tous les éléments déclarés comme **dllimport** ou `dllexport`. Toutes les déclarations incluses dans l'interface DLL doivent spécifier l'attribut **dllimport** ou `dllexport`. Toutefois, la définition peut spécifier uniquement l'attribut `dllexport`. Par exemple, la définition de fonction suivante génère une erreur de compilation :  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int func()    /* Error; dllimport prohibited in */  
                        /* definition. */  
{  
   return 1;  
}  
```  
  
 Le code suivant génère aussi une erreur :  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int i = 10;      /* Error; this is a definition. */  
```  
  
 Mais voici la syntaxe correcte :  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport int i = 10;      /* Okay: this is an export definition. */  
```  
  
 L'utilisation de `dllexport` implique une définition tandis que **dllimport** implique une déclaration. Vous devez utiliser le mot clé `extern` avec `dllexport` pour forcer une déclaration. Sinon, une définition est impliquée.  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
extern DllImport int k;   /* These are correct and imply */  
Dllimport int j;          /* a declaration. */      
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’importation et d’exportation de DLL](../c-language/dll-import-and-export-functions.md)