---
description: 'En savoir plus sur : erreur du compilateur C2708'
title: Erreur du compilateur C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: c965375c92c98a58a0fb6d0d51b3358e6b5798b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320868"
---
# <a name="compiler-error-c2708"></a>Erreur du compilateur C2708

'identificateur' : la longueur des paramètres réels en octets diffère de l’appel ou de la référence précédent

Une fonction [__stdcall](../../cpp/stdcall.md) doit être précédée d’un prototype. Sinon, le compilateur interprète le premier appel à la fonction comme un prototype et cette erreur se produit lorsque le compilateur rencontre un appel qui ne correspond pas.

Pour corriger cette erreur, ajoutez un prototype de fonction.
