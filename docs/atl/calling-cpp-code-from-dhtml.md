---
title: Appeler le Code C++ à partir de DHTML | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9e369396c68a041dc5fe027802859c6071e50e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355459"
---
# <a name="calling-c-code-from-dhtml"></a>Appel du Code C++ depuis DHTML
Un contrôle DHTML peut être hébergé dans un conteneur, comme le conteneur de Test ou d’Internet Explorer. Consultez [test des propriétés et des événements avec le conteneur de Test](../mfc/testing-properties-and-events-with-test-container.md) pour plus d’informations sur la façon d’accéder au conteneur de Test.  
  
 Le conteneur qui héberge le contrôle communique avec le contrôle à l’aide des interfaces de contrôle normal. DHTML utilise l’interface de dispatch qui se termine par « UI » pour communiquer avec votre code C++ et votre ressource HTML. Dans [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md), vous pouvez vous exercer à ajouter les méthodes à appeler par ces différentes interfaces.  
  
 Pour voir un exemple d’appel de code C++ à partir de DHTML, [créer un contrôle DHTML](../atl/creating-an-atl-dhtml-control.md) à l’aide de l’Assistant contrôle ATL et examinez le code dans le fichier d’en-tête et dans le fichier HTML.  
  
## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Déclarer des méthodes WebBrowser dans le fichier d’en-tête  
 Pour appeler les méthodes C++ depuis l’UI DHTML, vous devez ajouter des méthodes à l’interface utilisateur de votre contrôle. Par exemple, le fichier d’en-tête créé par l’Assistant contrôle ATL contient la méthode C++ `OnClick`, qui est un membre de l’interface de l’interface utilisateur du contrôle générées par l’Assistant.  
  
 Examinez `OnClick` dans le fichier .h du contrôle :  
  
 [!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]  
  
 Le premier paramètre, `pdispBody`, est un pointeur vers l’interface de dispatch de l’objet corps. Le deuxième paramètre, `varColor`, identifie la couleur à appliquer au contrôle.  
  
## <a name="calling-c-code-in-the-html-file"></a>Appel du Code C++ dans le fichier HTML  
 Une fois que vous avez déclaré les méthodes WebBrowser dans le fichier d’en-tête, vous pouvez appeler les méthodes à partir du fichier HTML. Notez dans le fichier HTML que l’Assistant contrôle ATL insère trois méthodes de dispatch Windows : trois `OnClick` méthodes qui distribuent les messages pour modifier la couleur d’arrière-plan du contrôle.  
  
 Examinez l’une des méthodes dans le fichier HTML :  
  
 `<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`  
  
 Dans le code HTML ci-dessus, la méthode externe de fenêtre, `OnClick`, est appelée dans le cadre de la légende du bouton. La méthode possède deux paramètres : `theBody`, qui référence le corps du document HTML, et `"red"`, ce qui signifie que couleur d’arrière-plan du contrôle deviendra rouge lorsque le bouton est activé. Le `Red` après la balise est l’étiquette du bouton.  
  
 Consultez [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md) pour plus d’informations sur l’envoi de vos propres méthodes. Consultez [identifier les éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) pour plus d’informations sur le fichier HTML.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)

