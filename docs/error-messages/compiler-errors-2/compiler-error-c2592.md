---
title: Erreur du compilateur C2592
ms.date: 11/04/2016
f1_keywords:
- C2592
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
ms.openlocfilehash: 914a03772b7c1675f5fee572fe1ca24f469e91f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177376"
---
# <a name="compiler-error-c2592"></a>Erreur du compilateur C2592

'classe' : 'base_class_2' est hérité de 'base_class_1' et ne peut pas être spécifié de nouveau

Vous ne pouvez spécifier que les classes de base qui n'héritent pas d'autres classes de base. Dans ce cas, seul `base_class_1` est nécessaire dans la spécification de `class` car `base_class_1` hérite déjà de `base_class_2`.
