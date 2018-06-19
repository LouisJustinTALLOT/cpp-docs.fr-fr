---
title: La modification du contrôle ATL DHTML | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3810236aca4661a6cdcd8399294cdb73e97948fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356493"
---
# <a name="modifying-the-atl-dhtml-control"></a>La modification du contrôle ATL DHTML
L’Assistant contrôle ATL fournit le code de démarrage vous pouvez générer et exécuter le contrôle, et donc vous pouvez voir la manière dont les méthodes sont écrites dans les fichiers projet et comment le DHTML appelle le code du contrôle C++ en utilisant les méthodes de distribution. Vous pouvez ajouter n’importe quelle méthode de répartition à l’interface. Ensuite, vous pouvez appeler les méthodes dans la ressource HTML.  
  
#### <a name="to-modify-the-atl-dhtml-control"></a>Pour modifier le contrôle ATL DHTML  
  
1.  Dans Affichage de classes, développez le projet de contrôle.  
  
     Notez que l’interface qui se termine par « UI » possède une méthode, `OnClick`. L’interface qui ne se termine pas dans l’interface « utilisateur » n’a pas de méthodes.  
  
2.  Ajoutez une méthode appelée `MethodInvoked` à l’interface qui ne se termine pas par « UI ».  
  
     Cette méthode sera ajoutée à l’interface qui est utilisé dans le conteneur de contrôle pour l’interaction du conteneur, pas à l’interface utilisée par le DHTML pour interagir avec le contrôle. Seul le conteneur peut appeler cette méthode.  
  
3.  Recherchez la méthode extraite dans le fichier .cpp et ajoutez du code pour afficher une boîte de message, par exemple :  
  
 [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  Ajoutez une autre méthode appelée `HelloHTML`, seulement cette fois-ci, ajoutez-le à l’interface qui se termine par « UI ». Rechercher les extraits `HelloHTML` méthode dans .cpp et ajoutez le code pour afficher une boîte de message, par exemple :  
  
 [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  Ajoutez une troisième méthode, `GoToURL`, à l’interface qui ne se termine pas par « UI ». Implémentez cette méthode en appelant [IWebBrowser2::Navigate](https://msdn.microsoft.com/library/aa752133.aspx), comme suit :  
  
 [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]  
  
     Vous pouvez utiliser la **IWebBrowser2** méthodes car ATL fournit un pointeur vers cette interface pour vous dans votre fichier .h.  
  
 Ensuite, modifiez la ressource HTML pour appeler les méthodes que vous avez créé. Vous allez ajouter trois boutons pour appeler ces méthodes.  
  
#### <a name="to-modify-the-html-resource"></a>Pour modifier la ressource HTML  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le fichier .htm pour afficher la ressource HTML.  
  
     Examinez le code HTML, notamment les appels aux méthodes de dispatch Windows externes. Le code HTML appelle du projet `OnClick` (méthode) et les paramètres indiquent le corps du contrôle (`theBody`) et la couleur à assigner («`red`»). Le texte qui suit l’appel de méthode est l’étiquette qui apparaît sur le bouton.  
  
2.  Ajoutez un autre `OnClick` (méthode), uniquement de modifier la couleur. Par exemple :  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
 ```  
  
     Cette méthode crée un bouton étiqueté **Actualiser**, que l’utilisateur peut cliquer pour retourner le contrôle à l’arrière-plan blanc d’origine.  
  
3.  Ajoutez l’appel à la `HelloHTML` méthode que vous avez créé. Par exemple :  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
 ```  
  
     Cette méthode crée un bouton étiqueté **HelloHTML**, que l’utilisateur peut cliquer pour afficher les `HelloHTML` boîte de message.  
  
 Vous pouvez à présent générer et [tester le contrôle DHTML modifié](../atl/testing-the-modified-atl-dhtml-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)

