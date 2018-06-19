---
title: Identification des éléments du projet de contrôle DHTML | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 525ad4e073607064234641f6544a11901ded0096
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357680"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identification des éléments du projet de contrôle DHTML
La plupart du code contrôle DHTML est identique à celui créé pour n’importe quel contrôle ATL. Pour comprendre le code générique, parcourez le [didacticiel ATL](../atl/active-template-library-atl-tutorial.md), et lisez les sections [création d’un projet ATL](../atl/reference/creating-an-atl-project.md) et [notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md).  
  
 Un contrôle DHTML est similaire à n’importe quel contrôle ATL, à l’exception :  
  
-   En plus des interfaces standards implémentées par un contrôle, il implémente une interface supplémentaire qui est utilisée pour la communication entre le code C++ et l’interface utilisateur HTML (IU). L’interface utilisateur HTML appelle du code C++ à l’aide de cette interface.  
  
-   Il crée une ressource HTML pour le contrôle de l’interface utilisateur.  
  
-   Il permet d’accéder au modèle objet DHTML via la variable membre `m_spBrowser`, qui est un pointeur intelligent de type [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx). Utilisez ce pointeur pour accéder à n’importe quelle partie du modèle d’objet DHTML.  
  
 Le graphique suivant illustre la relation entre votre DLL, le contrôle DHTML, le navigateur Web et la ressource HTML.  
  
 ![Éléments d’un projet de contrôle DHTML](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  Les noms sur cette illustration sont des espaces réservés. Les noms de votre ressource HTML et les interfaces exposées sur votre contrôle sont basées sur les noms que vous leur attribuez dans l’Assistant contrôle ATL.  
  
 Dans ce graphique, les éléments sont :  
  
-   **Ma DLL** la DLL créée à l’aide de l’Assistant Projet ATL.  
  
-   **Contrôle DHTML** (`m_spBrowser`) le contrôle DHTML créé à l’aide de l’Assistant objet ATL. Ce contrôle accède via l’interface de l’objet de navigateur Web, à l’objet du navigateur Web et ses méthodes **IWebBrowser2**. Le contrôle lui-même expose les deux interfaces suivantes, en plus des autres interfaces standards requises pour un contrôle.  
  
    -   **IDHCTL1** l’interface exposée par le contrôle pour une utilisation uniquement par le conteneur.  
  
    -   **IDHCTLUI1** l’interface de dispatch pour la communication entre le code C++ et l’interface utilisateur HTML. Le navigateur Web utilise l’interface de dispatch du contrôle pour afficher le contrôle. Vous pouvez appeler les différentes méthodes de cette interface de dispatch de l’interface utilisateur du contrôle en appelant `window.external`, suivi par le nom de méthode sur cette interface de dispatch que vous souhaitez appeler. Vous pouvez accéder à `window.external` à partir d’une balise SCRIPT dans le code HTML qui compose l’interface utilisateur pour ce contrôle. Pour plus d’informations sur l’appel de méthodes externes dans le fichier de ressources, consultez [appel du Code C++ depuis DHTML](../atl/calling-cpp-code-from-dhtml.md).  
  
-   **IDR_CTL1** l’ID de ressource de la ressource HTML. Son nom de fichier est dans ce cas, DHCTL1UI.htm. Le contrôle DHTML emploie une ressource HTML qui contient des balises HTML standard et des commandes de dispatch de fenêtre externes que vous pouvez modifier à l’aide de l’éditeur de texte.  
  
-   **Navigateur Web** le navigateur Web affiche l’UI du contrôle, selon le code HTML dans la ressource HTML. Un pointeur vers le navigateur **IWebBrowser2** interface est disponible dans le contrôle DHTML pour autoriser l’accès au modèle objet DHTML.  
  
 L’Assistant contrôle ATL génère un contrôle avec le code par défaut dans la ressource HTML et le fichier .cpp. Vous pouvez compiler et exécuter le contrôle tel que généré par l’Assistant, puis afficher le contrôle dans le navigateur Web ou le conteneur de Test du contrôle ActiveX. L’illustration ci-dessous montre la valeur par défaut du contrôle ATL DHTML avec trois boutons affichés dans le conteneur de Test :  
  
 ![Contrôle ATL DHTML](../atl/media/vc52en2.gif "vc52en2")  
  
 Consultez [création d’un contrôle ATL DHTML](../atl/creating-an-atl-dhtml-control.md) pour commencer la création d’un contrôle DHTML. Consultez [test des propriétés et des événements avec le conteneur de Test](../mfc/testing-properties-and-events-with-test-container.md) pour plus d’informations sur la façon d’accéder au conteneur de Test.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)

