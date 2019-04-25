---
title: Erreur du compilateur C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160952"
---
# <a name="compiler-error-c2708"></a>Erreur du compilateur C2708

'identificateur' : longueur en octets des paramètres réels diffère d’appel précédent ou de référence

Un [__stdcall](../../cpp/stdcall.md) fonction doit être précédée d’un prototype. Sinon, le compilateur interprète le premier appel à la fonction comme un prototype et cette erreur se produit lorsque le compilateur rencontre un appel qui ne correspond pas.

Pour résoudre ce problème, ajoutez un prototype de fonction.