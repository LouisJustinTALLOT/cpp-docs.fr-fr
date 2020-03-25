---
title: Avertissement du compilateur (niveau 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 7de4cdf0eacb1b9848a4350f1d223da1fd47d1fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198300"
---
# <a name="compiler-warning-level-4-c4611"></a>Avertissement du compilateur (niveau 4) C4611

l’interaction entre’Function' C++ et la destruction d’objet n’est pas portable

Sur certaines plateformes, les fonctions qui incluent **catch** peuvent C++ ne pas prendre en charge la sémantique d’objet de destruction lorsqu’elle est hors de portée.

Pour éviter un comportement inattendu, évitez d’utiliser **catch** dans les fonctions qui ont des constructeurs et des destructeurs.

Cet avertissement n’est émis qu’une seule fois ; consultez [pragma warning](../../preprocessor/warning.md).
