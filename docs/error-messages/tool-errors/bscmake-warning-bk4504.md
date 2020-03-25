---
title: Avertissement BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 57858827439ac8cc11e3718d7a484124ae8a6d74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197442"
---
# <a name="bscmake-warning-bk4504"></a>Avertissement BSCMAKE BK4504

le fichier contient un trop grand nombre de références ; autres références à partir de cette source ignorées

Le fichier. cpp contient plus de 64 000 références de symboles. Lorsque BSCMAKE a rencontré 64 000 références dans un fichier, il ignore toutes les références supplémentaires.

Pour corriger le problème, fractionnez le fichier en deux ou plusieurs fichiers, chacun d’entre eux ayant moins de 64 000 références de symboles, ou utilisez la directive de préprocesseur `#pragma component(browser)` pour limiter les symboles générés pour des références particulières. Pour plus d’informations, consultez [composant](../../preprocessor/component.md).
