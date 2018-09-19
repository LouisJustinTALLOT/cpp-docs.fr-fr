---
title: Erreur des LNK2039 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac4fdde90911427a1a193bfb6f3a950a7bdcf180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081791"
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