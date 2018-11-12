---
title: Blocs
ms.date: 11/04/2016
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
ms.openlocfilehash: c7ae46278fa76f2ca1a6f24a376f84dd77a97b16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477894"
---
# <a name="blocks"></a>Blocs

Une séquence de déclarations, de définitions et d'instructions placées entre accolades (**{ }**) est appelée un « bloc ». Il existe deux types de bloc en C. L'« instruction composée, » une instruction composée d'une ou plusieurs instructions (consultez [L'instruction composée](../c-language/compound-statement-c.md)), est un type de bloc. L’autre, la « définition de fonction », se compose d’une instruction composée (le corps de la fonction) et de l’« en-tête » associé de la fonction (le nom de la fonction, le type de retour et les paramètres formels). Un bloc au sein d'autres blocs est dit « imbriqué ».

Toutes les instructions composées sont placées entre accolades. En revanche, tous les éléments délimités par des accolades ne constituent pas une instruction composée. Par exemple, bien que les spécifications des éléments de tableau, de structure ou d'énumération puissent apparaître entre accolades, ce ne sont pas des instructions composées.

## <a name="see-also"></a>Voir aussi

[Fichiers sources et programmes sources](../c-language/source-files-and-source-programs.md)