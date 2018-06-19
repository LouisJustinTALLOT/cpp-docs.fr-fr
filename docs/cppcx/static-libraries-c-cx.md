---
title: Bibliothèques statiques (C + c++ / CX) | Documents Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ffa905cbe0fd49489bd3634cb927cce57ea4ddbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090101"
---
# <a name="static-libraries-ccx"></a>Bibliothèques statiques (C++/CX)
Une bibliothèque statique qui est utilisée dans une application de plateforme Windows universelle (UWP) peut contenir du code à la norme ISO C++, y compris les types STL et également les appels aux API Win32 qui ne sont pas exclus de la plateforme d’application Windows Runtime. Une bibliothèque statique consomme des composants Windows Runtime et peut créer des composants Windows Runtime avec certaines restrictions.  
  
## <a name="creating-static-libraries"></a>Création de bibliothèques statiques  
  
#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>Pour créer une bibliothèque statique pour une utilisation dans une application UWP  
  
1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**. Sous **Visual C++** > **Windows universel** choisissez **bibliothèque statique (Windows universel)**.  
  
2.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**. Dans le **propriétés** boîte de dialogue le **propriétés de Configuration** > **C/C++** , définissez **consommer l’Extension Windows Runtime** à **Oui (/ZW)**.  
  
 Lorsque vous compilez une nouvelle bibliothèque statique, si vous effectuez un appel à une API Win32 qui est exclue pour les applications UWP, le compilateur déclenche l’erreur C3861 « Identificateur introuvable ». Pour rechercher une autre méthode qui est pris en charge pour le Windows Runtime, consultez [Alternatives aux API Windows dans les applications UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
 Si vous ajoutez un projet de bibliothèque statique C++ à une solution d’application UWP, vous devrez peut-être mettre à jour les paramètres de propriété du projet de bibliothèque afin que la propriété de prise en charge de plateforme Windows universelle est définie **Oui**. Sans ce paramètre, le code est généré et des liens, mais une erreur se produit lorsque vous essayez de vérifier l’application pour Microsoft Store. La bibliothèque statique doit être compilée avec les mêmes paramètres de compilateur que ceux du projet qui la consomme.  
  
 Si vous consommez une bibliothèque statique qui crée des classes `ref` publiques, des classes d'interface publiques ou des classes de valeur publiques, l'éditeur de liens déclenche l'avertissement suivant :  
  
> **avertissement LNK4264 :** archivage du fichier objet compilé avec /ZW dans une bibliothèque statique ; Notez que lors de la création des types Windows Runtime, il n'est pas recommandée pour créer un lien avec une bibliothèque statique qui contient des métadonnées Windows Runtime.  
  
 Vous pouvez ignorer l’avertissement uniquement si la bibliothèque statique ne produise pas les composants Windows Runtime qui sont consommés en dehors de la bibliothèque elle-même. Si la bibliothèque ne consomme pas un composant qu'elle définit, l'éditeur de liens peut optimiser l'implémentation même si les métadonnées publiques contiennent les informations de type. En d'autres termes, les composants publics d'une bibliothèque statique sont compilés mais ne sont pas activés au moment de l'exécution. Pour cette raison, un composant Windows Runtime qui est destiné à la consommation par d’autres composants ou les applications doit être implémenté dans une bibliothèque de liens dynamiques (DLL).  
  
## <a name="see-also"></a>Voir aussi  
 [Thread et Marshaling](../cppcx/threading-and-marshaling-c-cx.md)