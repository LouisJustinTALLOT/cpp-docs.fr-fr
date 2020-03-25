---
title: Avertissement du compilateur (niveau 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c9bf60e8eec0ee6416bda3323583f3e056fce1a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174880"
---
# <a name="compiler-warning-level-1-c4819"></a>Avertissement du compilateur (niveau 1) C4819

> Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (*nombre*). Enregistrez le fichier au format Unicode pour éviter toute perte de données.

C4819 se produit lorsque vous compilez un fichier source ANSI sur un système à l’aide d’une page de codes qui ne peut pas représenter tous les caractères du fichier.

Il existe plusieurs façons de résoudre C4819. Une méthode simple consiste à supprimer le caractère incriminé, si vous n’en avez pas besoin, par exemple, s’il se trouve dans un commentaire. Vous pouvez définir la page de codes système dans le panneau de configuration sur un qui prend en charge le jeu de caractères utilisé par votre code source. Vous pouvez utiliser des [séquences d’échappement](/cpp/c-language/escape-sequences) Unicode pour créer des caractères ou des chaînes qui utilisent uniquement le jeu de caractères ANSI de base dans votre code source. Enfin, vous pouvez enregistrer le fichier au format Unicode avec une signature, également appelée marque d’ordre d’octet (BOM).

Pour enregistrer un fichier au format Unicode, dans Visual Studio, choisissez **fichier** > **Enregistrer sous**. Dans la boîte de dialogue **enregistrer le fichier sous** , sélectionnez la liste déroulante sur le bouton **Enregistrer** , puis choisissez **enregistrer avec encodage**. Si vous enregistrez dans le même nom de fichier, vous devrez peut-être confirmer que vous souhaitez remplacer le fichier. Dans la boîte de dialogue **options d’enregistrement avancées** , choisissez un encodage qui peut représenter tous les caractères du fichier (par exemple, **Unicode (UTF-8 avec signature)-CodePage 65001**), puis choisissez **OK**.
