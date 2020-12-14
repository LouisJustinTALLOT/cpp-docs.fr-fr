---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1123'
title: Erreur des outils Éditeur de liens LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: f9ee04a8e46c34e6ac5133c90488ed49619734d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281364"
---
# <a name="linker-tools-error-lnk1123"></a>Erreur des outils Éditeur de liens LNK1123

> échec lors de la conversion en fichier COFF : fichier non valide ou endommagé

Les fichiers d'entrée doivent avoir le format COFF (Common Object File Format). Si un fichier d'entrée n'est pas au format COFF, l'éditeur de liens essaie automatiquement de convertir les objets OMF 32 bits au format COFF, ou exécute CVTRES.EXE pour convertir les fichiers de ressources. Ce message indique que l'éditeur de liens n'a pas pu convertir le fichier. Cela peut également se produire lors de l'utilisation d'une version incompatible de CVTRES.EXE à partir d'une autre installation de Visual Studio, du Kit de développement Windows ou du .NET Framework.

> [!NOTE]
> Si vous exécutez une version antérieure de Visual Studio, il est possible que la conversion automatique ne soit pas prise en charge.

## <a name="to-fix-the-problem"></a>Pour corriger ce problème

- Appliquez l'ensemble des service packs et des mises à jour pour votre version de Visual Studio. Ceci est particulièrement important pour Visual Studio 2010.

- Tentez une génération après avoir désactivé les liens incrémentiels. Dans la barre de menus, choisissez **Projet**, **Propriétés**. Dans la boîte de dialogue **pages de propriétés** , développez **Propriétés de configuration**, éditeur de **liens**. Modifiez la valeur de **activer le lien incrémentiel** sur **non**.

- Vérifiez que la version de CVTRES.EXE trouvée en premier dans votre variable d’environnement PATH correspond à la version des outils de génération ou à la version de l’Ensemble d’outils de plateforme, utilisée par votre projet.

- Essayez de désactiver l'option Incorporer le manifeste. Dans la barre de menus, choisissez **Projet**, **Propriétés**. Dans la boîte de dialogue **pages de propriétés** , développez **Propriétés de configuration**, **outil manifeste**, **entrée et sortie**. Modifiez la valeur de **incorporer le manifeste** en **non**.

- Assurez-vous que le type de fichier est valide. Par exemple, assurez-vous qu'un objet OMF est un objet 32 bits et non pas 16 bits. Pour plus d’informations, consultez [. Fichiers obj en tant qu’entrée](../../build/reference/dot-obj-files-as-linker-input.md) de l’éditeur de liens et [format PE](/windows/win32/Debug/pe-format).

- Assurez-vous que le fichier n'est pas endommagé. Régénérez-le, si nécessaire.

## <a name="see-also"></a>Voir aussi

[. Fichiers obj en tant qu’entrée dans l’éditeur de liens](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[Référence EDITBIN](../../build/reference/editbin-reference.md)<br/>
[Référence DUMPBIN](../../build/reference/dumpbin-reference.md)
