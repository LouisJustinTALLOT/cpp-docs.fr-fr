---
title: Erreur irrécupérable RC1019 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1019
dev_langs:
- C++
helpviewer_keywords:
- RC1019
ms.assetid: 432fff44-04a9-4e13-91c6-870df6f0b4e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a455daffba3957b9a4628ecab9e604994e4a4ce2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027087"
---
# <a name="resource-compiler-fatal-error-rc1019"></a>Erreur irrécupérable RC1019 du compilateur de ressources 

inattendue ' #else '

Le `#else` directive ne figure pas dans un `#if`, **#ifdef**, ou **#ifndef** construire.

Assurez-vous qu’il existe un `#if`, **#ifdef**, ou **#ifndef** instruction en vigueur avant cette instruction.