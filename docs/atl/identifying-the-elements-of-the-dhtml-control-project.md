---
title: Identification des éléments du projet de contrôle DHTML
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: e38b94e200754ce9dd37df2bfb17dfaa32cafe49
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175705"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identification des éléments du projet de contrôle DHTML

La plupart des codes de contrôle DHTML Edit est identique à celui créé pour n’importe quel contrôle ATL. Pour obtenir une compréhension élémentaire du code générique, parcourez le [didacticiel ATL](../atl/active-template-library-atl-tutorial.md), et lisez les sections [création d’un projet ATL](../atl/reference/creating-an-atl-project.md) et [principes de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md).

Un contrôle DHTML Edit est similaire à n’importe quel contrôle ATL, à l’exception :

- En plus des interfaces standards qu'implémente un contrôle, il implémente une interface supplémentaire qui est utilisée pour la communication entre le code C++ et l’interface utilisateur HTML (IU). L’interface utilisateur HTML appelle du code C++ à l’aide de cette interface.

- Il crée une ressource HTML pour le contrôle de l’interface utilisateur.

- Il permet d’accéder au modèle d’objet DHTML via la variable membre `m_spBrowser`, qui est un pointeur intelligent de type [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx). Utilisez ce pointeur pour accéder à n’importe quelle partie du modèle d’objet DHTML.

Le graphique suivant illustre la relation entre votre DLL, le contrôle DHTML Edit, le navigateur Web et la ressource HTML.

![Éléments d’un projet de contrôle DHTML Edit](../atl/media/vc52en1.gif "éléments d’un projet de contrôle DHTML")

> [!NOTE]
>  Les noms de ce graphique sont des espaces réservés. Les noms de votre ressource HTML et les interfaces exposées sur votre contrôle sont basés sur les noms qu'affectez-les dans l’Assistant contrôle ATL.

Dans ce graphique, les éléments sont :

- **Ma DLL** la DLL créée à l’aide de l’Assistant Projet ATL.

- **Contrôle DHTML** (`m_spBrowser`) le contrôle DHTML créé à l’aide de l’Assistant objet ATL. Ce contrôle accède via l’interface de l’objet de navigateur Web, à l’objet du navigateur Web et ses méthodes `IWebBrowser2`. Le contrôle lui-même expose les deux interfaces suivantes, en plus des autres interfaces standards requises pour un contrôle.

   - `IDHCTL1` L’interface exposée par le contrôle pour une utilisation uniquement par le conteneur.

   - `IDHCTLUI1` Interface de dispatch pour la communication entre le code C++ et l’interface utilisateur HTML. Le navigateur Web utilise l’interface de dispatch du contrôle pour afficher le contrôle. Vous pouvez appeler diverses méthodes de cette interface de dispatch de l’interface utilisateur du contrôle en appelant `window.external`, suivi par le nom de méthode sur cette interface de dispatch que vous souhaitez appeler. Vous accédez à `window.external` à partir d’une balise de SCRIPT dans le code HTML qui compose l’interface utilisateur pour ce contrôle. Pour plus d’informations sur l’appel de méthodes externes dans le fichier de ressources, consultez [appel de Code C++ à partir de DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** l’ID de ressource de la ressource HTML. Son nom de fichier est dans ce cas, DHCTL1UI.htm. Le contrôle DHTML Edit utilise une ressource HTML qui contient des balises HTML standard et les commandes de dispatch de fenêtre externe que vous pouvez modifier à l’aide de l’éditeur de texte.

- **Navigateur Web** le navigateur Web affiche l’interface utilisateur du contrôle, selon le code HTML dans la ressource HTML. Un pointeur vers le navigateur Web `IWebBrowser2` interface est disponible dans le contrôle DHTML Edit pour autoriser l’accès au modèle d’objet DHTML.

L’Assistant contrôle ATL génère un contrôle avec le code par défaut dans la ressource HTML et le fichier .cpp. Vous pouvez compiler et exécuter le contrôle, telle que générée par l’Assistant et afficher ensuite le contrôle dans le navigateur Web ou le contrôle ActiveX Test Container. L’illustration ci-dessous montre la valeur par défaut du contrôle ATL DHTML avec trois boutons affichés dans le conteneur de Test :

![Contrôle ATL DHTML](../atl/media/vc52en2.gif "contrôle ATL DHTML")

Consultez [création d’un contrôle ATL DHTML](../atl/creating-an-atl-dhtml-control.md) pour commencer la création d’un contrôle DHTML Edit. Consultez [test des propriétés et des événements avec le conteneur de Test](../mfc/testing-properties-and-events-with-test-container.md) pour plus d’informations sur l’accès du conteneur de Test.

## <a name="see-also"></a>Voir aussi

[Prise en charge pour le contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)

