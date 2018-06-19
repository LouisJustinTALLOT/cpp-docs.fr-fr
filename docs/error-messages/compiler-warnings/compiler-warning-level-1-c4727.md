---
title: Compilateur avertissement (niveau 1) C4727 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4727
dev_langs:
- C++
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c92e42fe275f821e333a0f04a116034a5bb849a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282780"
---
# <a name="compiler-warning-level-1-c4727"></a>Avertissement du compilateur (niveau 1) C4727
« PCH nommé fichier_pch comportant le même horodatage dans fichier_obj_1 et fichier_obj_2.  Utilisation du premier PCH.  
  
 Erreur C4727 se produit lors de la compilation de plusieurs modules (compilands) avec **/Yc**, et où le compilateur n’a pas pu marquer tous les fichiers .obj avec le même horodatage .pch.  
  
 Pour résoudre, compilez un fichier source avec **/Yc /c** (crée un fichier .pch), et compilez les autres séparément avec **/Yu /c** (utilise un fichier .pch), puis les relier.  
  
 Par conséquent, si vous avez procédé comme et génère l’erreur C4727 :  
  
 **cl /clr /GL a.cpp b.cpp c.cpp /Ycstdafx.h**  
  
 Vous procéderiez comme suit à la place :  
  
 **cl /clr /GL a.cpp /Ycstdafx.h /c**  
  
 **cl /clr /GL b.cpp c.cpp /Yustdafx.h /link a.obj**  
  
 Pour plus d'informations, consultez  
  
-   [/Yc (Créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu (Utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md)