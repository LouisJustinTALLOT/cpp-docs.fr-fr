---
title: Erreur du compilateur C2592
ms.date: 11/04/2016
f1_keywords:
- C2592
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
ms.openlocfilehash: bcb65addd95364d0755408a96c859182703768ff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206833"
---
# <a name="compiler-error-c2592"></a>Erreur du compilateur C2592

'classe' : 'base_class_2' est hérité de 'base_class_1' et ne peut pas être spécifié de nouveau

Vous ne pouvez spécifier que les classes de base qui n'héritent pas d'autres classes de base. Dans ce cas, seul `base_class_1` est nécessaire dans la spécification de **`class`** , car `base_class_1` hérite déjà `base_class_2` .
