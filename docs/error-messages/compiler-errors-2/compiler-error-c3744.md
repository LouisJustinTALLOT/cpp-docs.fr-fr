---
title: Erreur du compilateur C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227105"
---
# <a name="compiler-error-c3744"></a>Erreur du compilateur C3744

__unhook doit avoir au moins 3 arguments pour les événements managés

Le [__unhook](../../cpp/unhook.md) fonction doit prendre trois paramètres lorsqu’il est utilisé dans un programme qui est compilé pour les Extensions managées pour C++.

`__hook` et `__unhook` ne sont pas compatibles avec la programmation /clr. Utilisez les opérateurs += et -= à la place.

C3744 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**.
