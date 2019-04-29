---
title: Avertissement BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279290"
---
# <a name="bscmake-warning-bk4504"></a>Avertissement BSCMAKE BK4504

fichier contient trop de références ; en ignorant les références ultérieures provenant de cette source

Le fichier .cpp contient plus de 64 000 références des symboles. Lors de la BSCMAKE a rencontré 64 000 références dans un fichier, il ignore toutes les références supplémentaires.

Pour corriger le problème, fractionnez le fichier en deux ou plusieurs fichiers, chacun d'entre eux ayant moins de 64 000 références de symboles, ou utilisent le `#pragma component(browser)` directive de préprocesseur limite les symboles qui sont générés pour les références particuliers. Pour plus d’informations, consultez [composant](../../preprocessor/component.md).