---
title: hdrstop | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs:
- C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1c628efaf45be87dcfc046cf1774c762c157f4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847024"
---
# <a name="hdrstop"></a>hdrstop
Vous permet de mieux contrôler les noms des fichiers de précompilation et l'emplacement auquel l'état de compilation est enregistré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## <a name="remarks"></a>Notes  
 Le *nom de fichier* est le nom du fichier d’en-tête précompilé à utiliser ou créer (selon que [/Yu](../build/reference/yu-use-precompiled-header-file.md) ou [/Yc](../build/reference/yc-create-precompiled-header-file.md) est spécifié). Si *nom de fichier* ne contient pas une spécification de chemin d’accès, le fichier d’en-tête précompilé est censé pour se trouver dans le même répertoire que le fichier source.  
  
 Si un fichier C ou C++ contient une **hdrstop** pragma lors de la compilation avec/Yc, le compilateur enregistre l’état de la compilation jusqu'à l’emplacement du pragma. L'état compilé de tout code qui suit le pragma n'est pas enregistré.  
  
 Utilisez *nom de fichier* pour nommer le fichier d’en-tête précompilé dans lequel l’état compilé est enregistré. Un espace entre **hdrstop** et *nom de fichier* est facultatif. Le nom de fichier spécifié dans le **hdrstop** pragma est une chaîne et est donc soumis aux contraintes de n’importe quelle chaîne C ou C++. En particulier, vous devez le placer entre guillemets et utiliser le caractère d'échappement (barre oblique inverse) pour spécifier des noms de répertoires. Par exemple :  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 Le nom du fichier d'en-tête précompilé est déterminé selon les règles suivantes par ordre de priorité :  
  
1.  L’argument de l’option du compilateur /Fp  
  
2.  Le *nom de fichier* argument #**pragma hdrstop**  
  
3.  Le nom de base du fichier source avec une extension .PCH  
  
 Pour les options /Yc et /Yu, si aucune des options de deux compilation ni le **hdrstop** pragma spécifie un nom de fichier, le nom de base du fichier source est utilisé comme nom de base du fichier d’en-tête précompilé.  
  
 Vous pouvez également utiliser les commandes de prétraitement pour remplacer une macro comme suit :  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 Les règles suivantes régissent où le **hdrstop** pragma peut être placé :  
  
-   Il doit apparaître hors de toute déclaration ou définition de données ou de fonction.  
  
-   Il doit être spécifié dans le fichier source, pas dans un fichier d'en-tête.  
  
## <a name="example"></a>Exemple  
  
```  
#include <windows.h>                 // Include several files  
#include "myhdr.h"  
  
__inline Disp( char *szToDisplay )   // Define an inline function  
{  
    ...                              // Some code to display string  
}  
#pragma hdrstop  
```  
  
 Dans cet exemple, le **hdrstop** pragma apparaît une fois que les deux fichiers ont été ajoutés et une fonction inline a été définie. Au départ, cela peut sembler être un positionnement étrange pour le pragma. Utilisez, toutefois, que les options de précompilation manuelles, /Yc et/Yu, avec la **hdrstop** pragma permet à vous permet de précompiler des fichiers source entiers, même du code incorporé. Le compilateur Microsoft ne se limite pas à précompiler uniquement les déclarations de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)