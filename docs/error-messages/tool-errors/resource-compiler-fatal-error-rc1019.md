---
title: Erreur irrécupérable RC1019 du compilateur de ressources | Documents Microsoft
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
ms.openlocfilehash: 1cd9658a97f1f62a2a5a262e7262127744dd144a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319733"
---
# <a name="resource-compiler-fatal-error-rc1019"></a>Erreur irrécupérable RC1019 du compilateur de ressources 
inattendue ' #else '  
  
 Le `#else` directive ne figure pas dans un `#if`, **#ifdef**, ou **#ifndef** construire.  
  
 Assurez-vous qu’il existe un `#if`, **#ifdef**, ou **#ifndef** instruction en vigueur avant cette instruction.