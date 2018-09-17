---
title: Est en conflit avec le x86 compilateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f01e65adfb42a5fb3361e75ce34060f7dc1b9f9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709668"
---
# <a name="conflicts-with-the-x86-compiler"></a>Conflits avec le compilateur x86

Types de données qui sont supérieurs à 4 octets ne sont pas alignées automatiquement sur la pile lorsque vous utilisez le x86 compilateur de compiler une application. Étant donné que l’architecture pour le x86 compilateur est une pile alignée sur 4 octets, toute valeur supérieure à 4 octets, par exemple, un entier 64 bits, ne peut pas être alignée automatiquement à une adresse de 8 octets.

Utilisation des données non alignées a deux conséquences.

- Il peut prendre plus de temps à accéder à des emplacements non alignés que nécessaire pour accéder aux emplacements alignés.

- Emplacements non alignés ne peut pas être utilisés dans les opérations verrouillées.

Si vous avez besoin d’un alignement plus strict, utilisez `__declspec(align(N)) on your variable declarations`. Cela indique au compilateur d’aligner dynamiquement de la pile pour répondre à vos spécifications. Toutefois, ajuster de façon dynamique la pile au moment de l’exécution peut provoquer une exécution plus lente de votre application.

## <a name="see-also"></a>Voir aussi

[Types et stockage](../build/types-and-storage.md)<br/>
[align](../cpp/align-cpp.md)