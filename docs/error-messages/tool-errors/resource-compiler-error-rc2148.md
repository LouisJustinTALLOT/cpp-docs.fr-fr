---
title: Erreur RC2148 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2148
dev_langs:
- C++
helpviewer_keywords:
- RC2148
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b78bf8e9eb9ebe86dae75856ea3c0b6f5d34a26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075903"
---
# <a name="resource-compiler-error-rc2148"></a>Erreur RC2148 du compilateur de ressources 

ID de sous-langue trop grande

La valeur d’ID de sous-langue était hors limites.

L’instruction **LANGUAGE** doit utiliser la syntaxe suivante :

**LANGUAGE** *ID_langue_principale*,*ID_langue_secondaire*

ID de sous-langue valides sont définis en tant que **SUBLANG_** constantes dans le fichier WINNT.h.