---
title: Erreur du compilateur C2708 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0accd68881cccad5e34530a6c157a4e8179b283
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111093"
---
# <a name="compiler-error-c2708"></a>Erreur du compilateur C2708

'identificateur' : longueur en octets des paramètres réels diffère d’appel précédent ou de référence

Un [__stdcall](../../cpp/stdcall.md) fonction doit être précédée d’un prototype. Sinon, le compilateur interprète le premier appel à la fonction comme un prototype et cette erreur se produit lorsque le compilateur rencontre un appel qui ne correspond pas.

Pour résoudre ce problème, ajoutez un prototype de fonction.