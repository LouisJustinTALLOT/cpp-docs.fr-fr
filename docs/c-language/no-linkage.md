---
title: Aucune liaison
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: 9775270c5c1fb0b6758f994c432104d75e19d38d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505077"
---
# <a name="no-linkage"></a>Aucune liaison

Si une déclaration d'un identificateur dans un bloc n'inclut pas le spécificateur de classe de stockage `extern`, l'identificateur n'a aucune liaison et est propre à la fonction.

Les identificateurs suivants n'ont aucune liaison :

- Un identificateur déclaré comme autre chose qu'un objet ou une fonction

- un identificateur déclaré comme étant un paramètre de fonction

- Un identificateur de portée de bloc pour un objet déclaré sans spécificateur de classe de stockage `extern`

Si un identificateur n'a aucune liaison, une nouvelle déclaration du même nom (dans un spécificateur de déclarateur ou de type) au même niveau de portée génère une erreur de redéfinition de symbole.

## <a name="see-also"></a>Voir aussi

[Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)