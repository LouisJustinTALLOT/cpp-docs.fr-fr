---
title: Avertissement du compilateur (niveau 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349670"
---
# <a name="compiler-warning-level-4-c4611"></a>Avertissement du compilateur (niveau 4) C4611

interaction entre 'fonction' et la destruction d’objets C++ n’est pas portable

Sur certaines plateformes, les fonctions qui incluent **catch** peut prend pas en charge la sémantique d’objet C++ de destruction lorsque hors de portée.

Pour éviter un comportement inattendu, évitez d’utiliser **catch** dans les fonctions qui possèdent des constructeurs et destructeurs.

Cet avertissement est émis uniquement une seule fois ; consultez [pragma avertissement](../../preprocessor/warning.md).