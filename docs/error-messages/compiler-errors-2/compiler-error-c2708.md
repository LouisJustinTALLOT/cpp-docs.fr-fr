---
title: Erreur du compilateur C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460071"
---
# <a name="compiler-error-c2708"></a>Erreur du compilateur C2708

'identificateur' : longueur en octets des paramètres réels diffère d’appel précédent ou de référence

Un [__stdcall](../../cpp/stdcall.md) fonction doit être précédée d’un prototype. Sinon, le compilateur interprète le premier appel à la fonction comme un prototype et cette erreur se produit lorsque le compilateur rencontre un appel qui ne correspond pas.

Pour résoudre ce problème, ajoutez un prototype de fonction.