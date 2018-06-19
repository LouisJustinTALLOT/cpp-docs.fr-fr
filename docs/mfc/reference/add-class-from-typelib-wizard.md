---
title: Assistant Ajout de classes d’une Typelib | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4eaf4b800fdc1954c54043aa7e2669613e6b27e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351951"
---
# <a name="add-class-from-typelib-wizard"></a>Assistant Ajout de classes d'une Typelib
Utilisez cet Assistant pour ajouter une classe MFC à partir d’une bibliothèque de types disponibles. L’Assistant crée une classe pour chaque interface que vous ajoutez à partir de la bibliothèque de types sélectionnée.  
  
 **Ajouter une classe à partir de**  
 Spécifie l’emplacement de la bibliothèque de types à partir de laquelle la classe est créée.  
  
|Option|Description|  
|------------|-----------------|  
|**Registry**|La bibliothèque de types est enregistrée dans le système. Bibliothèques de types inscrits sont répertoriés dans **bibliothèques de types disponibles**.|  
|**Fichier**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais est contenue dans un fichier. Vous devez fournir l’emplacement du fichier dans **emplacement**.|  
  
 **Bibliothèques de types disponibles**  
 Répertorie les bibliothèques de types actuellement inscrits dans le système. Sélectionnez une bibliothèque de types à partir de cette liste pour afficher ses interfaces dans les **Interfaces** liste.  
  
 Consultez « À l’intérieur de Distributed COM : Type Libraries and Language Integration » dans MSDN library pour plus d’informations sur l’inscription des bibliothèques de types.  
  
 **Emplacement**  
 Spécifie l’emplacement de la bibliothèque de types. Si vous cliquez sur **fichier** sous **ajouter une classe à partir**, vous pouvez fournir l’emplacement du fichier contenant la bibliothèque de types. Pour accéder à l’emplacement du fichier, cliquez sur le bouton de sélection.  
  
 **Interfaces**  
 Répertorie les interfaces dans la bibliothèque de types actuellement sélectionné dans le **bibliothèques de types disponibles** liste.  
  
|Bouton de transfert|Description|  
|---------------------|-----------------|  
|**>**|Ajoute l’interface actuellement sélectionné dans le **Interfaces** liste. Estompé si aucune interface n’est sélectionnée.|  
|**>>**|Ajoute toutes les interfaces dans la bibliothèque de types actuellement sélectionnée dans le **bibliothèques de types disponibles** liste.|  
|**<**|Supprime la classe actuellement sélectionnée dans le **classes générées** liste. Estompé si aucune classe n’est actuellement sélectionné dans le **classes générées** liste.|  
|**<\<**|Supprime toutes les classes dans le **classes générées** liste. If grisé le **classes générées** liste est vide.|  
  
 **Classes générées**  
 Spécifie les noms de classe à générer à partir des interfaces ajoutées à l’aide de la **>** ou **>>** bouton. Vous pouvez cliquer sur cette zone pour sélectionner une classe, puis haut ou bas pour faire défiler la liste, afficher chaque nom de classe dans le `Class` boîte et nom de fichier dans le **fichier** boîte généré par l’Assistant lorsque vous cliquez sur  **Terminer**. Vous pouvez sélectionner qu’une seule classe à la fois dans cette zone.  
  
 Vous pouvez supprimer une classe en la sélectionnant dans cette liste en cliquant sur **<**. Vous n’avez pas besoin de sélectionner une classe dans la zone de classes générées pour supprimer toutes les classes ; en cliquant sur **<<**, vous supprimez toutes les classes dans le **classes générées** boîte.  
  
 `Class`  
 Spécifie le nom de la classe sélectionnée dans la **classes générées** zone que l’Assistant ajoute lorsque vous cliquez sur **Terminer**. Vous pouvez modifier le nom dans la `Class` boîte.  
  
 **Fichier**  
 Définit le nom du fichier d’en-tête pour la nouvelle classe. Par défaut, ce nom est basé sur le nom que vous fournissez dans **classes générées**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant enregistrera pas à l’emplacement sélectionné jusqu'à ce que vous cliquez sur **Terminer** dans l’Assistant.  
  
 L’Assistant ne remplacera pas un fichier. Si vous sélectionnez le nom d’un fichier existant, lorsque vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour ajouter le fichier ; cliquez sur **non** pour revenir à l’Assistant et spécifiez un autre nom de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe MFC à partir d’une bibliothèque de types](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Clients Automation : utilisation des bibliothèques de types](../../mfc/automation-clients-using-type-libraries.md)

