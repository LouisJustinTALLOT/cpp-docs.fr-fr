---
title: Erreur irrécupérable C1210 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1210
dev_langs:
- C++
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d22a34f44fb2c97fe341cb313d7917a35506cdd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704982"
---
# <a name="fatal-error-c1210"></a>Erreur irrécupérable C1210

> /clr:pure et /clr:safe ne sont pas pris en charge par la version installée du runtime

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

L’erreur C1210 se produit quand vous avez un compilateur pour la version actuelle, mais un Common Language Runtime d’une version précédente.

Certaines fonctionnalités du compilateur risquent de ne pas fonctionner sur une version précédente du runtime.

Pour remédier à l’erreur C1210, installez la version du Common Language Runtime prévue pour votre compilateur.