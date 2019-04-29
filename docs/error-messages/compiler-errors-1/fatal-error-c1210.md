---
title: Erreur irrécupérable C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: a90ca3e3b55642f1a6cd847997b83e4b7db46818
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385847"
---
# <a name="fatal-error-c1210"></a>Erreur irrécupérable C1210

> /clr:pure et /clr:safe ne sont pas pris en charge par la version installée du runtime

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

L’erreur C1210 se produit quand vous avez un compilateur pour la version actuelle, mais un Common Language Runtime d’une version précédente.

Certaines fonctionnalités du compilateur risquent de ne pas fonctionner sur une version précédente du runtime.

Pour remédier à l’erreur C1210, installez la version du Common Language Runtime prévue pour votre compilateur.