---
title: Aucune liaison
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: c80cb814145ac986864fe351e664d8472f3bf880
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232387"
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
