---
description: 'En savoir plus sur : erreur du compilateur C2856'
title: Erreur du compilateur C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 8594bc5902e13967084aa3695131d616a4cf04da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337549"
---
# <a name="compiler-error-c2856"></a>Erreur du compilateur C2856

\#pragma hdrstop ne peut pas se trouver à l’intérieur d’un bloc #if

Le `hdrstop` pragma ne peut pas être placé dans le corps d’un bloc de compilation conditionnelle.

Déplacez l' `#pragma hdrstop` instruction vers une zone qui n’est pas contenue dans un `#if/#endif` bloc.
