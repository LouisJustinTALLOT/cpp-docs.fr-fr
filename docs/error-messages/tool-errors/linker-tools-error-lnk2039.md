---
title: Erreur des outils Éditeur de liens LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: fad8960424cd73240d547ef894b2ae5cdf358601
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498274"
---
# <a name="linker-tools-error-lnk2039"></a>Erreur des outils Éditeur de liens LNK2039

l’importation de la classe ref\<type >' qui est définie dans another.obj ; il doit être importé ou définie, mais pas les deux

La classe ref ' <`type`>' est importé dans le fichier .obj spécifié mais est également défini dans un autre fichier .obj. Cette condition peut entraîner Échec d’exécution ou tout autre comportement inattendu.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez si «`type`» doit être défini dans l’autre fichier .obj et vérifier si elle doit être importé à partir du fichier .winmd.

1. Supprimer la définition ou l’importation.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Erreur des outils Éditeur de liens LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)