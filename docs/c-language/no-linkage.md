---
title: Aucune liaison
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: 69ead5d12d6689370e9ae04a54d5f5a8db06eca5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500749"
---
# <a name="no-linkage"></a>Aucune liaison

Si une déclaration d’un identificateur dans un bloc n’inclut pas le **`extern`** spécificateur de classe de stockage, l’identificateur n’a aucune liaison et est unique à la fonction.

Les identificateurs suivants n'ont aucune liaison :

- Un identificateur déclaré comme autre chose qu'un objet ou une fonction

- un identificateur déclaré comme étant un paramètre de fonction

- Identificateur de portée de bloc pour un objet déclaré sans spécificateur de **`extern`** classe de stockage

Si un identificateur n'a aucune liaison, une nouvelle déclaration du même nom (dans un spécificateur de déclarateur ou de type) au même niveau de portée génère une erreur de redéfinition de symbole.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/extern-cpp.md)
