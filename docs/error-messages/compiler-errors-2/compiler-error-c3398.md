---
description: 'En savoir plus sur : erreur du compilateur C3398'
title: Erreur du compilateur C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: 024390ec03ad145f418f79d2db3228bd790a6de7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321939"
---
# <a name="compiler-error-c3398"></a>Erreur du compilateur C3398

'operator' : impossible de convertir de 'function_signature' en 'function_pointer'. L'expression source doit être un symbole de fonction

Quand la convention d’appel [__clrcall](../../cpp/clrcall.md) n’est pas spécifiée lors de la compilation avec **/clr**, le compilateur génère deux points d’entrée (adresses) pour chaque fonction : un point d’entrée natif et un point d’entrée managé.

Par défaut, le compilateur retourne le point d’entrée natif, mais dans certains cas, il est souhaitable d’avoir un point d’entrée managé (par exemple, lors de l’assignation de l’adresse à un pointeur de fonction `__clrcall` ). Pour que le compilateur puisse choisir de manière fiable le point d’entrée managé dans une assignation, le côté droit doit être un symbole de fonction.
