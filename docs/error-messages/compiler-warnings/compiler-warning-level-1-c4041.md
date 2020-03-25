---
title: Avertissement du compilateur (niveau 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 14ea6d9cae3b490107b656153bb68815026971e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164233"
---
# <a name="compiler-warning-level-1-c4041"></a>Avertissement du compilateur (niveau 1) C4041

limite du compilateur : arrêt de la sortie de l’explorateur

Les informations du navigateur dépassent la limite du compilateur.

Cet avertissement peut être dû à une compilation avec [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informations du navigateur comprenant des variables locales).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Compilez avec /Fr (informations du navigateur sans variables locales).

1. Désactivez la sortie de navigateur (compilez sans /FR ou /Fr).
