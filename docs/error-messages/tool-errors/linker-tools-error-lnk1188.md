---
title: LNK1188 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31943ae253a332576fba73102db410b103a0096
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302618"
---
# <a name="linker-tools-error-lnk1188"></a>Erreur des outils Éditeur de liens LNK1188
BADFIXUPSECTION :: cible de correction non valide 'symbole' ; possible de section de longueur zéro  
  
 Au cours d’un lien VxD, la cible d’un réadressage n’avait pas une section. Avec LINK386 (une version antérieure), un enregistrement OMF GROUP (généré par une directive MASM GROUP) a peut-être été utilisé pour combiner la section de longueur zéro avec une autre section de longueur non nulle. Le format COFF ne prend pas en charge la directive GROUP et sections de longueur nulle. Quand LINK convertit automatiquement ce type d’objet OMF au format COFF, cette erreur peut se produire.