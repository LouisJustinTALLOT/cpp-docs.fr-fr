---
description: 'En savoir plus sur : erreur irrécupérable C1026'
title: Erreur irrécupérable C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: 08816f21879cf6dfbeb0389700d9a8ffdc7a40d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345509"
---
# <a name="fatal-error-c1026"></a>Erreur irrécupérable C1026

dépassement de capacité de la pile de l'analyseur, programme trop complexe

L’espace requis pour analyser le programme a provoqué un dépassement de capacité de la pile du compilateur.

Réduisez la complexité des expressions en procédant comme suit :

- Diminution de l’imbrication dans **`for`** les **`switch`** instructions et. Placez des instructions plus profondément imbriquées dans des fonctions distinctes.

- Fractionnement des expressions longues qui impliquent des opérateurs virgules ou des appels de fonction.
