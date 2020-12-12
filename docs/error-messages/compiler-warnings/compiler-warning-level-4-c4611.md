---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4611'
title: Avertissement du compilateur (niveau 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: df53392b2d56b9afb1ab0cbcb2fc7b6267d5f00f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168265"
---
# <a name="compiler-warning-level-4-c4611"></a>Avertissement du compilateur (niveau 4) C4611

l’interaction entre’Function’et la destruction d’objet C++ n’est pas portable

Sur certaines plateformes, les fonctions qui incluent **`catch`** peuvent ne pas prendre en charge la sémantique d’objet C++ en dehors de l’étendue.

Pour éviter un comportement inattendu, évitez **`catch`** d’utiliser dans les fonctions qui ont des constructeurs et des destructeurs.

Cet avertissement n’est émis qu’une seule fois ; consultez [pragma warning](../../preprocessor/warning.md).
