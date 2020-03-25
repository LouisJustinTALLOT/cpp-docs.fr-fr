---
title: Erreur du compilateur C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a1d3379a0da42c5aabd38cffbf6f6a3f340ef3b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202369"
---
# <a name="compiler-error-c2708"></a>Erreur du compilateur C2708

'identificateur' : la longueur des paramètres réels en octets diffère de l’appel ou de la référence précédent

Une fonction [__stdcall](../../cpp/stdcall.md) doit être précédée d’un prototype. Sinon, le compilateur interprète le premier appel à la fonction comme un prototype et cette erreur se produit lorsque le compilateur rencontre un appel qui ne correspond pas.

Pour corriger cette erreur, ajoutez un prototype de fonction.
