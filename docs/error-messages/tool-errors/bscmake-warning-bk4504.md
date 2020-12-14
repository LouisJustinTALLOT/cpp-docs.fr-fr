---
description: 'En savoir plus sur : BSCMAKE Warning BK4504'
title: Avertissement BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 8b07c15b03a040ea19ec368c6f869d02f3e36f79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237827"
---
# <a name="bscmake-warning-bk4504"></a>Avertissement BSCMAKE BK4504

le fichier contient un trop grand nombre de références ; autres références à partir de cette source ignorées

Le fichier. cpp contient plus de 64 000 références de symboles. Lorsque BSCMAKE a rencontré 64 000 références dans un fichier, il ignore toutes les références supplémentaires.

Pour corriger le problème, fractionnez le fichier en deux ou plusieurs fichiers, chacun d’entre eux ayant moins de 64 000 références de symboles, ou utilisez la `#pragma component(browser)` directive de préprocesseur pour limiter les symboles générés pour des références particulières. Pour plus d’informations, consultez [composant](../../preprocessor/component.md).
