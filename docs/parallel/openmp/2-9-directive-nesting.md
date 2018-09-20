---
title: 2.9 imbrication de directives | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9558180a2f063171be563219f89ec3858e37a5d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396985"
---
# <a name="29-directive-nesting"></a>2.9 Imbrication de directives

L’imbrication dynamique de directives doit respecter les règles suivantes :

- Un **parallèles** directive dynamiquement à l’intérieur d’un autre **parallèles** logiquement établit une nouvelle équipe, qui se compose du thread actuel uniquement, à moins qu’imbriqués de parallélisme est activée.

- **pour**, **sections**, et **unique** directives lier au même **parallèles** ne sont pas autorisés à être imbriqués les uns des autres.

- **critique** directives portant le même nom ne sont pas autorisés à être imbriqués les uns des autres. Notez que cette restriction n’est pas suffisante pour empêcher tout interblocage.

- **pour**, **sections**, et **unique** directives ne sont pas autorisés dans l’étendue dynamique de **critique**, **classés**, et **master** régions si les directives lié à la même **parallèles** en tant que les régions.

- **cloisonnement** directives ne sont pas autorisés dans l’étendue dynamique de **pour**, **classés**, **sections**, **unique**, **master**, et **critique** régions si les directives lié à la même **parallèles** en tant que les régions.

- **maître** directives ne sont pas autorisés dans l’étendue dynamique de **pour**, **sections**, et **unique** directives si le **master** directives lier au même **parallèles** en tant que les directives de partage de travail.

- **classés** directives ne sont pas autorisés dans l’étendue dynamique de **critique** régions si les directives lié à la même **parallèles** en tant que les régions.

- N’importe quelle directive qui est autorisé lors de l’exécution dynamiquement à l’intérieur d’une région parallèle est également autorisée lors de l’exécution en dehors d’une région parallèle. Lors de l’exécution dynamiquement en dehors d’une région parallèle spécifié par l’utilisateur, la directive est exécutée par une équipe composée du thread principal uniquement.