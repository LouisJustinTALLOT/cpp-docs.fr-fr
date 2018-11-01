---
title: Erreur des outils Éditeur de liens LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 69ac20522aebb7391319c0de210e06b305f3fd0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461254"
---
# <a name="linker-tools-error-lnk1188"></a>Erreur des outils Éditeur de liens LNK1188

BADFIXUPSECTION :: cible de correction non valide 'symbol' ; possible de section de longueur zéro

Au cours d’un lien VxD, la cible d’un réadressage n’avait pas d’une section. Avec LINK386 (une version antérieure), un enregistrement OMF GROUP (généré par une directive MASM GROUP) ont été utilisé pour combiner la section de longueur zéro par une autre section de longueur non nulle. Le format COFF ne prend pas en charge la directive de groupe et de sections de longueur nulle. Lorsque le lien convertit automatiquement ce type d’objet OMF au format COFF, cette erreur peut se produire.