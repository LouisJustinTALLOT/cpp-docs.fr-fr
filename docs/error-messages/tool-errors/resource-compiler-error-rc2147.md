---
title: Erreur RC2147 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2147
dev_langs:
- C++
helpviewer_keywords:
- RC2147
ms.assetid: 09974f06-1731-4e70-b373-f9218e0ee8d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f3ca510dfd61e92a33f599c7ef261e03b8ad2cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032840"
---
# <a name="resource-compiler-error-rc2147"></a>Erreur RC2147 du compilateur de ressources 

ID de sous-langue pas un nombre

La valeur d’ID de sous-langue doit être un nombre.

L’instruction **LANGUAGE** doit utiliser la syntaxe suivante :

**LANGUAGE** *ID_langue_principale*,*ID_langue_secondaire*

ID de sous-langue valides sont définis en tant que **SUBLANG_** constantes dans le fichier WINNT.h.