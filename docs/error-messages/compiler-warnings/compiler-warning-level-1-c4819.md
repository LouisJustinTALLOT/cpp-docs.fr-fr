---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4819'
title: Avertissement du compilateur (niveau 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: 871a861f7860f8561fb830cc6a19980af7726174
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198217"
---
# <a name="compiler-warning-level-1-c4819"></a>Avertissement du compilateur (niveau 1) C4819

> Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (*nombre*). Enregistrez le fichier au format Unicode pour éviter toute perte de données.

C4819 se produit lorsque vous compilez un fichier source ANSI sur un système à l’aide d’une page de codes qui ne peut pas représenter tous les caractères du fichier.

Il existe plusieurs façons de résoudre C4819. Une méthode simple consiste à supprimer le caractère incriminé, si vous n’en avez pas besoin, par exemple, s’il se trouve dans un commentaire. Vous pouvez définir la page de codes système dans le panneau de configuration sur un qui prend en charge le jeu de caractères utilisé par votre code source. Vous pouvez utiliser des [séquences d’échappement](../../c-language/escape-sequences.md) Unicode pour créer des caractères ou des chaînes qui utilisent uniquement le jeu de caractères ANSI de base dans votre code source. Enfin, vous pouvez enregistrer le fichier au format Unicode avec une signature, également appelée marque d’ordre d’octet (BOM).

Pour enregistrer un fichier au format Unicode, dans Visual Studio, choisissez **fichier**  >  **Enregistrer sous**. Dans la boîte de dialogue **enregistrer le fichier sous** , sélectionnez la liste déroulante sur le bouton **Enregistrer** , puis choisissez **enregistrer avec encodage**. Si vous enregistrez dans le même nom de fichier, vous devrez peut-être confirmer que vous souhaitez remplacer le fichier. Dans la boîte de dialogue **options d’enregistrement avancées** , choisissez un encodage qui peut représenter tous les caractères du fichier (par exemple, **Unicode (UTF-8 avec signature)-CodePage 65001**), puis choisissez **OK**.
