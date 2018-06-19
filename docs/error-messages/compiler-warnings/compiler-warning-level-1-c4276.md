---
title: Compilateur avertissement (niveau 1) C4276 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afedab27c2fb93075aa33053c12ec6973824f144
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277304"
---
# <a name="compiler-warning-level-1-c4276"></a>Avertissement du compilateur (niveau 1) C4276
'fonction' : aucun prototype fourni ; ne supposé aucun paramètre  
  
 Lorsque vous prenez l’adresse d’une fonction avec la [__stdcall](../../cpp/stdcall.md) convention d’appel, vous devez donner un prototype afin que le compilateur puisse créer le nom décoré de la fonction. Étant donné que *fonction* a pas de prototype, le compilateur, lors de la création du nom décoré, suppose que la fonction n’a aucun paramètre.