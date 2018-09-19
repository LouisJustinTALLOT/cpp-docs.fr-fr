---
title: Erreur des LNK1123 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1123
dev_langs:
- C++
helpviewer_keywords:
- LNK1123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0b2c7f89e7ad7d0142cb6830c4d4c3361b014c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075838"
---
# <a name="linker-tools-error-lnk1123"></a>Erreur des outils Éditeur de liens LNK1123

> échec lors de la conversion en fichier COFF : fichier non valide ou endommagé

Les fichiers d'entrée doivent avoir le format COFF (Common Object File Format). Si un fichier d'entrée n'est pas au format COFF, l'éditeur de liens essaie automatiquement de convertir les objets OMF 32 bits au format COFF, ou exécute CVTRES.EXE pour convertir les fichiers de ressources. Ce message indique que l'éditeur de liens n'a pas pu convertir le fichier. Cela peut également se produire lors de l'utilisation d'une version incompatible de CVTRES.EXE à partir d'une autre installation de Visual Studio, du Kit de développement Windows ou du .NET Framework.

> [!NOTE]
> Si vous exécutez une version antérieure de Visual Studio, il est possible que la conversion automatique ne soit pas prise en charge.

## <a name="to-fix-the-problem"></a>Pour corriger ce problème

- Appliquez l'ensemble des service packs et des mises à jour pour votre version de Visual Studio. Ceci est particulièrement important pour Visual Studio 2010.

- Tentez une génération après avoir désactivé les liens incrémentiels. Dans la barre de menus, choisissez **Projet**, **Propriétés**. Dans le **Pages de propriétés** boîte de dialogue, développez **propriétés de Configuration**, **l’éditeur de liens**. Modifiez la valeur de **activation des liens incrémentiels** à **non**.

- Vérifiez que la version de CVTRES.EXE trouvée en premier dans votre variable d’environnement PATH correspond à la version des outils de génération ou à la version de l’Ensemble d’outils de plateforme, utilisée par votre projet.

- Essayez de désactiver l'option Incorporer le manifeste. Dans la barre de menus, choisissez **Projet**, **Propriétés**. Dans le **Pages de propriétés** boîte de dialogue, développez **propriétés de Configuration**, **outil manifeste**, **d’entrée et sortie**. Modifiez la valeur de **incorporer le manifeste** à **non**.

- Assurez-vous que le type de fichier est valide. Par exemple, assurez-vous qu'un objet OMF est un objet 32 bits et non pas 16 bits. Pour plus d’informations, consultez [. Fichiers obj en tant qu’entrée de l’éditeur de liens](../../build/reference/dot-obj-files-as-linker-input.md) et [Format PE](/windows/desktop/Debug/pe-format).

- Assurez-vous que le fichier n'est pas endommagé. Régénérez-le, si nécessaire.

## <a name="see-also"></a>Voir aussi

[Fichiers .obj en tant qu’entrée dans l’éditeur de liens](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[Informations de référence sur EDITBIN](../../build/reference/editbin-reference.md)<br/>
[Informations de référence sur DUMPBIN](../../build/reference/dumpbin-reference.md)
