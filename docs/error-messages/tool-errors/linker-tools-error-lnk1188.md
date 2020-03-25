---
title: Erreur des outils Éditeur de liens LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: b18a93c7434ee3d66f42829f373bd916a65369bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195173"
---
# <a name="linker-tools-error-lnk1188"></a>Erreur des outils Éditeur de liens LNK1188

BADFIXUPSECTION :: cible de correction non valide’Symbol'; section de longueur zéro possible

Pendant un lien VxD, la cible d’un déplacement n’avait pas de section. Avec LINK386 (une version antérieure), un enregistrement de groupe OMF (généré par une directive de groupe MASM) peut avoir été utilisé pour combiner la section de longueur zéro et une autre section de longueur différente de zéro. Le format COFF ne prend pas en charge la directive de groupe et les sections de longueur nulle. Quand LINK convertit automatiquement ce type d’objets OMF en COFF, cette erreur peut se produire.
