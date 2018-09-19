---
title: Suppression de fichiers ouverts | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], deleting
ms.assetid: 4fba7fb2-df0a-458e-b760-8858e12b855c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8e66c811571f22c263193ffad676052b34b7f72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087095"
---
# <a name="deleting-open-files"></a>Suppression de fichiers ouverts

**ANSI 4.9.4.1** L'effet de la fonction remove sur un fichier ouvert

La fonction remove supprime un fichier. Si le fichier est ouvert, cette fonction échoue et retourne -1.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)