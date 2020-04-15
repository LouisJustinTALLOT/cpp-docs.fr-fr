---
title: Identifier les éléments du projet de contrôle DHTML
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 5fabdc815989c21bdf6b0932b9d6826e28d7012a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319504"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identifier les éléments du projet de contrôle DHTML

La plupart des codes de contrôle DHTML est exactement comme celui créé pour n’importe quel contrôle ATL. Pour une compréhension de base du code générique, travailler à travers le [tutoriel ATL](../atl/active-template-library-atl-tutorial.md), et lire les sections [Création d’un projet ATL](../atl/reference/creating-an-atl-project.md) et [les principes fondamentaux de ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md).

Un contrôle DHTML est similaire à tout contrôle ATL, sauf:

- En plus des interfaces régulières qu’un contrôle implémente, il implémente une interface supplémentaire qui est utilisée pour communiquer entre le code C ET l’interface utilisateur HTML (interface utilisateur HTML). L’interface HTML appelle dans le code C à l’aide de cette interface.

- Il crée une ressource HTML pour l’interface utilisateur de contrôle.

- Il permet l’accès au modèle d’objet DHTML à travers la variable `m_spBrowser`membre , qui est un pointeur intelligent de type [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)). Utilisez ce pointeur pour accéder à n’importe quelle partie du modèle d’objet DHTML.

Le graphique suivant illustre la relation entre votre DLL, le contrôle DHTML, le navigateur Web et la ressource HTML.

![Éléments d'un projet de contrôle DHTML](../atl/media/vc52en1.gif "Éléments d'un projet de contrôle DHTML")

> [!NOTE]
> Les noms sur ce graphique sont des placeholders. Les noms de votre ressource HTML et les interfaces exposées sur votre contrôle sont basés sur les noms que vous leur attribuez dans le assistant de contrôle ATL.

Dans ce graphique, les éléments sont :

- **Mon DLL** Le DLL créé à l’aide de l’ASSISTANT de projet ATL.

- **DHTML** Control`m_spBrowser`( ) Le contrôle DHTML, créé à l’aide de l’assistant d’objets ATL. Ce contrôle accède à l’objet du navigateur Web et `IWebBrowser2`à ses méthodes via l’interface de l’objet du navigateur Web. Le contrôle lui-même expose les deux interfaces suivantes, en plus des autres interfaces standard requises pour un contrôle.

  - `IDHCTL1`L’interface exposée par le contrôle pour une utilisation uniquement par le conteneur.

  - `IDHCTLUI1`L’interface de répartition pour communiquer entre le code C et l’interface utilisateur HTML. Le navigateur Web utilise l’interface de répartition du contrôle pour afficher le contrôle. Vous pouvez appeler différentes méthodes de cette interface de répartition `window.external`à partir de l’interface utilisateur du contrôle en invoquant , suivie par le nom de la méthode sur cette interface de répartition que vous souhaitez invoquer. Vous accédez à `window.external` partir d’une balise SCRIPT dans le HTML qui constitue l’interface utilisateur pour ce contrôle. Pour plus d’informations sur l’invocation de méthodes externes dans le fichier des ressources, voir [Appeler le code CMD de DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** L’ID de ressource de la ressource HTML. Son nom de fichier, dans ce cas, est DHCTL1UI.htm. Le contrôle DHTML utilise une ressource HTML qui contient des balises HTML standard et des commandes externes de répartition des fenêtres que vous pouvez modifier à l’aide de l’éditeur de texte.

- **Navigateur Web** Le navigateur Web affiche l’interface utilisateur du contrôle, basé sur le HTML dans la ressource HTML. Un pointeur sur l’interface du `IWebBrowser2` navigateur Web est disponible dans le contrôle DHTML pour permettre l’accès au modèle d’objet DHTML.

L’assistant de contrôle ATL génère un contrôle avec code par défaut à la fois dans la ressource HTML et le fichier .cpp. Vous pouvez compiler et exécuter le contrôle tel que généré par l’assistant, puis afficher le contrôle dans le navigateur Web ou le conteneur de contrôle ActiveX. L’image ci-dessous montre le contrôle PAR défaut ATL DHTML avec trois boutons affichés dans Test Container:

![Contrôle ATL DHTML](../atl/media/vc52en2.gif "Contrôle ATL DHTML")

Voir [Créer un contrôle ATL DHTML](../atl/creating-an-atl-dhtml-control.md) pour commencer à construire un contrôle DHTML. Consultez [les propriétés et les événements de test avec le conteneur d’essai](../mfc/testing-properties-and-events-with-test-container.md) pour obtenir de l’information sur la façon d’accéder au conteneur d’essai.

## <a name="see-also"></a>Voir aussi

[Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)
