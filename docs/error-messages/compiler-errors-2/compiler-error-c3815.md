---
title: Erreur du compilateur C3815 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3815
dev_langs:
- C++
helpviewer_keywords:
- C3815
ms.assetid: c5a3b404-6341-4fd3-92af-152b404c4dde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae6d1244374ce7f83a5c309dac99f4eb36906caf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086939"
---
# <a name="compiler-error-c3815"></a>Erreur du compilateur C3815

type de retour de méthode 'accesseur_get' doit correspondre le type du dernier paramètre d’un accesseur Set

Lors de la déclaration des propriétés, la valeur de retour de la `get_accessor` méthode doit correspondre au dernier paramètre dans la déclaration de la méthode d’accesseur set.

C3815 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**.
