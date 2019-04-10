---
title: Avertissement du compilateur (niveau 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: d43b49d473e7113d8cdfb89aaa6e93045e13d0f7
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424220"
---
# <a name="compiler-warning-level-1-c4819"></a>Avertissement du compilateur (niveau 1) C4819

> Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (*nombre*). Enregistrez le fichier au format Unicode pour éviter toute perte de données.

L’erreur C4819 se produit lorsque vous compilez un fichier de source ANSI sur un système à l’aide d’une page de codes qui ne peut pas représenter tous les caractères dans le fichier.

Il existe plusieurs façons de résoudre l’erreur C4819. Un moyen simple consiste à supprimer le caractère incriminé, si vous n’en avez besoin, par exemple, si elle est dans un commentaire. Vous pouvez définir la page de codes système dans le panneau de contrôle pour qu’il prend en charge le jeu de caractères utilisé par votre code source. Vous pouvez utiliser Unicode [séquences d’échappement](/cpp/c-language/escape-sequences) pour créer caractères ou chaînes qui utilisent uniquement la base ANSI jeu de caractères dans votre code source. Enfin, vous pouvez enregistrer le fichier au format Unicode avec une signature, également appelé une marque d’ordre d’octet (BOM).

Pour enregistrer un fichier au format Unicode, dans Visual Studio, choisissez **fichier** > **Enregistrer sous**. Dans le **enregistrer le fichier sous** boîte de dialogue, sélectionnez la liste déroulante sur le **enregistrer** bouton et choisissez **enregistrer avec encodage**. Si vous enregistrez sur le même nom de fichier, vous devrez peut-être confirmer que vous souhaitez remplacer le fichier. Dans le **Options d’enregistrement avancées** boîte de dialogue, choisir l’encodage qui peut représenter tous les caractères dans le fichier, par exemple, **Unicode (UTF-8 avec signature) - page de codes 65001**, puis choisissez  **OK**.