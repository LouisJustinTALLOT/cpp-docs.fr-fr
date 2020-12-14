---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4985'
title: Avertissement du compilateur (niveau 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: c00c6ebd16f5160ffed726eae5307d7f3642eb3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234564"
---
# <a name="compiler-warning-level-4-c4985"></a>Avertissement du compilateur (niveau 4) C4985

> '*Symbol-Name*' : attributs absents de la déclaration précédente.

Les annotations du langage d’annotation de code source Microsoft (SAL) dans la définition ou la déclaration de méthode actuelle diffèrent des annotations d’une déclaration précédente. Les mêmes annotations SAL doivent être utilisées dans la définition et les déclarations d’une méthode.

Le langage d’annotation de code source Microsoft (SAL) propose un ensemble d’annotations qui décrivent la manière dont une fonction exploite ses paramètres, les hypothèses qu’elle émet à leur sujet et les garanties apportées lors de la finition. Les annotations sont définies dans le fichier d’en-tête sal.h.

Notez que les macros SAL ne sont pas développées, sauf si l’indicateur est spécifié pour le projet [`/analyze`](../../build/reference/analyze-code-analysis.md) . Lorsque vous spécifiez **`/analyze`** , le compilateur peut lever C4985, même si aucun avertissement ou erreur n’est apparu sans **`/analyze`** .

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Utilisez les mêmes annotations SAL dans la définition d’une méthode et toutes ses déclarations.

## <a name="see-also"></a>Voir aussi

[Annotations SAL](../../c-runtime-library/sal-annotations.md)
