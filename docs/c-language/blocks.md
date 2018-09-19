---
title: Blocs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9704b499106fc59364f5cc9ae97277939e835a77
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025320"
---
# <a name="blocks"></a>Blocs

Une séquence de déclarations, de définitions et d'instructions placées entre accolades (**{ }**) est appelée un « bloc ». Il existe deux types de bloc en C. L'« instruction composée, » une instruction composée d'une ou plusieurs instructions (consultez [L'instruction composée](../c-language/compound-statement-c.md)), est un type de bloc. L’autre, la « définition de fonction », se compose d’une instruction composée (le corps de la fonction) et de l’« en-tête » associé de la fonction (le nom de la fonction, le type de retour et les paramètres formels). Un bloc au sein d'autres blocs est dit « imbriqué ».

Toutes les instructions composées sont placées entre accolades. En revanche, tous les éléments délimités par des accolades ne constituent pas une instruction composée. Par exemple, bien que les spécifications des éléments de tableau, de structure ou d'énumération puissent apparaître entre accolades, ce ne sont pas des instructions composées.

## <a name="see-also"></a>Voir aussi

[Fichiers sources et programmes sources](../c-language/source-files-and-source-programs.md)