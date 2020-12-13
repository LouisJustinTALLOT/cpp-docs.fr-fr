---
description: 'En savoir plus sur : identification des éléments du projet de contrôle DHTML'
title: Identification des éléments du projet de contrôle DHTML
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 7f04857378564a86fc875e9874b79f6ae6c6a625
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148016"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identification des éléments du projet de contrôle DHTML

La plupart du code de contrôle DHTML est exactement similaire à celui créé pour un contrôle ATL. Pour une compréhension élémentaire du code générique, utilisez le [Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)et lisez les sections [création d’un projet ATL](../atl/reference/creating-an-atl-project.md) et [notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md).

Un contrôle DHTML est semblable à n’importe quel contrôle ATL, à l’exception des éléments suivants :

- Outre les interfaces régulières qu’un contrôle implémente, il implémente une interface supplémentaire utilisée pour communiquer entre le code C++ et l’interface utilisateur HTML. L’interface utilisateur HTML appelle du code C++ à l’aide de cette interface.

- Elle crée une ressource HTML pour l’interface utilisateur du contrôle.

- Il permet d’accéder au modèle objet DHTML via la variable membre `m_spBrowser` , qui est un pointeur intelligent de type [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)). Utilisez ce pointeur pour accéder à n’importe quelle partie du modèle d’objet DHTML.

Le graphique suivant illustre la relation entre votre DLL, le contrôle DHTML, le navigateur Web et la ressource HTML.

![Éléments d'un projet de contrôle DHTML](../atl/media/vc52en1.gif "Éléments d'un projet de contrôle DHTML")

> [!NOTE]
> Les noms de ce graphique sont des espaces réservés. Les noms de votre ressource HTML et des interfaces exposées sur votre contrôle sont basés sur les noms que vous leur affectez dans l’Assistant contrôle ATL.

Dans ce graphique, les éléments sont les suivants :

- **Ma dll** DLL créée à l’aide de l’Assistant Projet ATL.

- **Contrôle DHTML** ( `m_spBrowser` ) contrôle DHTML, créé à l’aide de l’Assistant objet ATL. Ce contrôle accède à l’objet de navigateur Web et à ses méthodes par le biais de l’interface de l’objet de navigateur Web, `IWebBrowser2` . Le contrôle lui-même expose les deux interfaces suivantes, en plus des autres interfaces standard requises pour un contrôle.

  - `IDHCTL1` Interface exposée par le contrôle pour une utilisation uniquement par le conteneur.

  - `IDHCTLUI1` Interface de dispatch pour la communication entre le code C++ et l’interface utilisateur HTML. Le navigateur Web utilise l’interface de dispatch du contrôle pour afficher le contrôle. Vous pouvez appeler diverses méthodes de cette interface de dispatch à partir de l’interface utilisateur du contrôle en appelant `window.external` , suivi du nom de la méthode sur cette interface de dispatch que vous souhaitez appeler. Vous pouvez accéder `window.external` à à partir d’une balise de script dans le code HTML qui compose l’interface utilisateur pour ce contrôle. Pour plus d’informations sur l’appel de méthodes externes dans le fichier de ressources, consultez [appel de code C++ à partir de DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** ID de ressource de la ressource HTML. Son nom de fichier, dans le cas présent, est DHCTL1UI.htm. Le contrôle DHTML utilise une ressource HTML qui contient des balises HTML standard et des commandes de dispatch de fenêtre externes que vous pouvez modifier à l’aide de l’éditeur de texte.

- **Navigateur Web** Le navigateur Web affiche l’interface utilisateur du contrôle, en fonction du code HTML de la ressource HTML. Un pointeur vers l’interface du navigateur Web `IWebBrowser2` est disponible dans le contrôle DHTML pour permettre l’accès au modèle objet DHTML.

L’Assistant contrôle ATL génère un contrôle avec le code par défaut à la fois dans la ressource HTML et dans le fichier. cpp. Vous pouvez compiler et exécuter le contrôle tel qu’il est généré par l’Assistant, puis afficher le contrôle dans le navigateur Web ou dans le conteneur de test de contrôle ActiveX. L’image ci-dessous montre le contrôle ATL DHTML par défaut avec trois boutons affichés dans Test Container :

![Contrôle ATL DHTML](../atl/media/vc52en2.gif "Contrôle ATL DHTML")

Consultez [création d’un contrôle ATL DHTML](../atl/creating-an-atl-dhtml-control.md) pour commencer à créer un contrôle DHTML. Pour plus d’informations sur l’accès à un conteneur de test, consultez Test des [Propriétés et des événements avec le conteneur](../mfc/testing-properties-and-events-with-test-container.md) de test.

## <a name="see-also"></a>Voir aussi

[Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)
