---
title: Erreur du compilateur C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: 3b688012009a87c1e3d0db05e47133893daeaf34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300451"
---
# <a name="compiler-error-c3398"></a>Erreur du compilateur C3398

'operator' : impossible de convertir de 'function_signature' en 'function_pointer'. L'expression source doit être un symbole de fonction

Quand la convention d’appel [__clrcall](../../cpp/clrcall.md) n’est pas spécifiée lors de la compilation avec **/clr**, le compilateur génère deux points d’entrée (adresses) pour chaque fonction : un point d’entrée natif et un point d’entrée managé.

Par défaut, le compilateur retourne le point d’entrée natif, mais dans certains cas, il est souhaitable d’avoir un point d’entrée managé (par exemple, lors de l’assignation de l’adresse à un pointeur de fonction `__clrcall` ). Pour que le compilateur puisse choisir de manière fiable le point d’entrée managé dans une assignation, le côté droit doit être un symbole de fonction.