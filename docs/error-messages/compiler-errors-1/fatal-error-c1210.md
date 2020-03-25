---
title: Erreur irrécupérable C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: 50bafa522c931c909b5ce163a78305ffc028765a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203383"
---
# <a name="fatal-error-c1210"></a>Erreur irrécupérable C1210

> /clr:pure et /clr:safe ne sont pas pris en charge par la version installée du runtime

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

L’erreur C1210 se produit quand vous avez un compilateur pour la version actuelle, mais un Common Language Runtime d’une version précédente.

Certaines fonctionnalités du compilateur risquent de ne pas fonctionner sur une version précédente du runtime.

Pour remédier à l’erreur C1210, installez la version du Common Language Runtime prévue pour votre compilateur.
