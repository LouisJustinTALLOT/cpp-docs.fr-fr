---
title: Erreur des LNK1188 des outils Éditeur de liens | Microsoft Docs
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
ms.openlocfilehash: 36b31590d94d809c16ed64d16071db0919f60238
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098938"
---
# <a name="linker-tools-error-lnk1188"></a>Erreur des outils Éditeur de liens LNK1188

BADFIXUPSECTION :: cible de correction non valide 'symbol' ; possible de section de longueur zéro

Au cours d’un lien VxD, la cible d’un réadressage n’avait pas d’une section. Avec LINK386 (une version antérieure), un enregistrement OMF GROUP (généré par une directive MASM GROUP) ont été utilisé pour combiner la section de longueur zéro par une autre section de longueur non nulle. Le format COFF ne prend pas en charge la directive de groupe et de sections de longueur nulle. Lorsque le lien convertit automatiquement ce type d’objet OMF au format COFF, cette erreur peut se produire.