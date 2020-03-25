---
title: Erreur des outils Éditeur de liens LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 7712747deb865ec62fa007fcd95ad09630d00cea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194497"
---
# <a name="linker-tools-error-lnk2039"></a>Erreur des outils Éditeur de liens LNK2039

importation de la classe ref'\<type > 'définie dans un autre. obj ; elle doit être importée ou définie, mais pas les deux

La classe ref « <`type`> » est importée dans le fichier. obj spécifié, mais elle est également définie dans un autre fichier. obj. Cette condition peut entraîner un échec d’exécution ou un autre comportement inattendu.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez si'`type`'doit être défini dans l’autre fichier. objet vérifiez s’il doit être importé à partir du fichier. winmd.

1. Supprimez la définition ou l’importation.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Erreur des outils Éditeur de liens LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
