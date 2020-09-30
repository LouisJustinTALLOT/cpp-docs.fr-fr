---
title: Conformité ANSI C
description: Vue d’ensemble des conventions d’affectation de noms Microsoft C Runtime pour la conformité ANSI C.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Ansi
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
ms.openlocfilehash: 39a3f9299be7dbef4783faa8e6d08fe6ad8461f5
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590301"
---
# <a name="ansi-c-compliance"></a>Conformité ANSI C

La convention d’affectation de noms pour tous les identificateurs spécifiques à Microsoft dans le système d’exécution (par exemple, les fonctions, macros, constantes, variables et définitions de type) est compatible ANSI. Dans cette documentation, toute fonction du Runtime qui suit les normes ANSI/ISO C est indiquée comme étant compatible ANSI. Les applications compatibles ANSI doivent utiliser uniquement ces fonctions compatibles ANSI.

Les noms des fonctions spécifiques à Microsoft et les variables globales commencent par un trait de soulignement simple. Ces noms ne peuvent être remplacés que localement, dans la portée de votre code. Par exemple, lorsque vous incluez des fichiers d’en-tête de Runtime Microsoft, vous pouvez toujours substituer localement la fonction spécifique à Microsoft nommée `_open` en déclarant une variable locale du même nom. Toutefois, vous ne pouvez pas utiliser ce nom pour votre propre fonction globale ou variable globale.

Les noms de macros spécifiques et constantes manifestes spécifiques à Microsoft commencent par deux traits de soulignement, ou avec un seul trait de soulignement suivi immédiatement d’une lettre majuscule. L’étendue de ces identificateurs est absolue. Par exemple, vous ne pouvez pas utiliser l’identificateur spécifique à Microsoft **_UPPER** pour cette raison.

## <a name="see-also"></a>Voir aussi

[Compatibilité](../c-runtime-library/compatibility.md)
