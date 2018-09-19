---
title: Erreur RC2144 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2144
dev_langs:
- C++
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f9eb2b25919a2336c36a459ef41eece447a490
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080491"
---
# <a name="resource-compiler-error-rc2144"></a>Erreur RC2144 du compilateur de ressources 

L'ID DE LANGUE PRINCIPALE n'est pas un numéro

L'ID DE LANGUE PRINCIPALE doit être un ID de langue hexadécimal. Consultez [chaînes de langues et pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) dans le *Run-Time Library Reference* pour obtenir la liste des ID de langue valide.

Cette erreur peut aussi se produire si des ressources ont été ajoutées et supprimées à partir du fichier .RC à l'aide d'un outil. Pour résoudre ce problème, ouvrez le fichier .RC dans un éditeur de texte et nettoyez manuellement les ressources non utilisées.