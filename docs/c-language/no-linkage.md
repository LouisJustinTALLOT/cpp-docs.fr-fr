---
title: Aucune liaison
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: a7c9a5b8f0ba92830500e55818093981a044d2df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218804"
---
# <a name="no-linkage"></a>Aucune liaison

Si une déclaration d’un identificateur dans un bloc n’inclut pas le **`extern`** spécificateur de classe de stockage, l’identificateur n’a aucune liaison et est unique à la fonction.

Les identificateurs suivants n'ont aucune liaison :

- Un identificateur déclaré comme autre chose qu'un objet ou une fonction

- un identificateur déclaré comme étant un paramètre de fonction

- Identificateur de portée de bloc pour un objet déclaré sans spécificateur de **`extern`** classe de stockage

Si un identificateur n'a aucune liaison, une nouvelle déclaration du même nom (dans un spécificateur de déclarateur ou de type) au même niveau de portée génère une erreur de redéfinition de symbole.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)
