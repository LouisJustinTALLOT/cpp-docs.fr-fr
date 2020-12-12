---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1188'
title: Erreur des outils Éditeur de liens LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 1bd826c3734d8079b370712ae829a0d0fb1abded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321837"
---
# <a name="linker-tools-error-lnk1188"></a>Erreur des outils Éditeur de liens LNK1188

BADFIXUPSECTION :: cible de correction non valide’Symbol'; section de longueur zéro possible

Pendant un lien VxD, la cible d’un déplacement n’avait pas de section. Avec LINK386 (une version antérieure), un enregistrement de groupe OMF (généré par une directive de groupe MASM) peut avoir été utilisé pour combiner la section de longueur zéro et une autre section de longueur différente de zéro. Le format COFF ne prend pas en charge la directive de groupe et les sections de longueur nulle. Quand LINK convertit automatiquement ce type d’objets OMF en COFF, cette erreur peut se produire.
