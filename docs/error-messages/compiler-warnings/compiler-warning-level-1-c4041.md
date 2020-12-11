---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4041'
title: Avertissement du compilateur (niveau 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: d3473be35182f6c99541aa2a0fc79de79dee4a07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160712"
---
# <a name="compiler-warning-level-1-c4041"></a>Avertissement du compilateur (niveau 1) C4041

limite du compilateur : arrêt de la sortie de l’explorateur

Les informations du navigateur dépassent la limite du compilateur.

Cet avertissement peut être dû à une compilation avec [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informations du navigateur comprenant des variables locales).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Compilez avec /Fr (informations du navigateur sans variables locales).

1. Désactivez la sortie de navigateur (compilez sans /FR ou /Fr).
