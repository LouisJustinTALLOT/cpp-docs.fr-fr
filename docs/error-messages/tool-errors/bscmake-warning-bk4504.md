---
title: Avertissement BSCMAKE BK4504 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a2da8903dade37faf3b14175b65f3169efd908
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049764"
---
# <a name="bscmake-warning-bk4504"></a>Avertissement BSCMAKE BK4504

fichier contient trop de références ; en ignorant les références ultérieures provenant de cette source

Le fichier .cpp contient plus de 64 000 références des symboles. Lors de la BSCMAKE a rencontré 64 000 références dans un fichier, il ignore toutes les références supplémentaires.

Pour corriger le problème, fractionnez le fichier en deux ou plusieurs fichiers, chacun d'entre eux ayant moins de 64 000 références de symboles, ou utilisent le `#pragma component(browser)` directive de préprocesseur limite les symboles qui sont générés pour les références particuliers. Pour plus d’informations, consultez [composant](../../preprocessor/component.md).