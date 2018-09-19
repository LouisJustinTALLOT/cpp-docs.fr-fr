---
title: Erreur du compilateur C3398 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 336494ea9581289efd9a41e604a28984125ae61a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018130"
---
# <a name="compiler-error-c3398"></a>Erreur du compilateur C3398

'operator' : impossible de convertir de 'function_signature' en 'function_pointer'. L'expression source doit être un symbole de fonction

Quand la convention d’appel [__clrcall](../../cpp/clrcall.md) n’est pas spécifiée lors de la compilation avec **/clr**, le compilateur génère deux points d’entrée (adresses) pour chaque fonction : un point d’entrée natif et un point d’entrée managé.

Par défaut, le compilateur retourne le point d’entrée natif, mais dans certains cas, il est souhaitable d’avoir un point d’entrée managé (par exemple, lors de l’assignation de l’adresse à un pointeur de fonction `__clrcall` ). Pour que le compilateur puisse choisir de manière fiable le point d’entrée managé dans une assignation, le côté droit doit être un symbole de fonction.