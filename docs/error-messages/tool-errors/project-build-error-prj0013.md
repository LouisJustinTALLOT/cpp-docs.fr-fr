---
title: Erreur de génération PRJ0013 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0013
dev_langs:
- C++
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7a151ca34d680a517c405e5cb6f91c18d35bedd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102643"
---
# <a name="project-build-error-prj0013"></a>Erreur de génération de projet PRJ0013

Les ressources système sont peut-être dangereusement basses. Impossible de créer un canal requis au lancement d'une génération.

Cette erreur indique que les ressources système sont basses. Pour résoudre cette erreur, réduisez l'utilisation des ressources système par les autres processus/applications.

Cette erreur peut également se produire si votre niveau de sécurité est insuffisant pour créer des canaux (consultez [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).