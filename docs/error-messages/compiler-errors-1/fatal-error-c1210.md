---
description: 'En savoir plus sur : erreur irrécupérable C1210'
title: Erreur irrécupérable C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: 6437d5894b0f3b4156dedc53f1a121ba85e7516f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267948"
---
# <a name="fatal-error-c1210"></a>Erreur irrécupérable C1210

> /clr:pure et /clr:safe ne sont pas pris en charge par la version installée du runtime

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

L’erreur C1210 se produit quand vous avez un compilateur pour la version actuelle, mais un Common Language Runtime d’une version précédente.

Certaines fonctionnalités du compilateur risquent de ne pas fonctionner sur une version précédente du runtime.

Pour remédier à l’erreur C1210, installez la version du Common Language Runtime prévue pour votre compilateur.
