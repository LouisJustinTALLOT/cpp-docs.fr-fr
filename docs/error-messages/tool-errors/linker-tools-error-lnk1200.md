---
title: LNK1200 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab32939c55dce5e27f907f3d23e639b24741cdc3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298822"
---
# <a name="linker-tools-error-lnk1200"></a>Erreur des outils Éditeur de liens LNK1200
Erreur de lecture de base de données du programme 'nom_fichier'  
  
 La base de données du programme (PDB) n’a pas pu être lu.  
  
 Cette erreur peut être dû à l’endommagement du fichier.  
  
 Si `filename` est le fichier PDB d’un fichier objet, recompilez le fichier objet à l’aide [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Si `filename` est le fichier PDB pour le fichier de sortie principal, et cette erreur s’est produite lors d’une édition de liens incrémentielle, supprimez le PDB et rétablir.