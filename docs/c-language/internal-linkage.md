---
title: Liaison interne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09b5a02b7892bff0233e37bbd63020a4d2904ec3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094206"
---
# <a name="internal-linkage"></a>Liaison interne

Si la déclaration d'un identificateur de portée de fichier pour un objet ou une fonction contient le *storage-class-specifier* **static**, l'identificateur a une liaison interne. Sinon, l'identificateur a une liaison externe. Consultez [Classes de stockage](../c-language/c-storage-classes.md) pour plus d'informations sur l'élément non terminal *storage-class-specifier*.

Dans une unité de traduction, chaque instance d'un identificateur avec une liaison interne désigne le même identificateur ou la même fonction. Les identificateurs liés en interne sont spécifiques à une unité de traduction.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)