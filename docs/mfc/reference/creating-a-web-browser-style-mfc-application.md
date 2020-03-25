---
title: Création d'une application MFC de style navigateur Web
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: e02e928f65ab4cd918e730135abc62ed3237decf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215122"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Création d'une application MFC de style navigateur Web

Une application de type navigateur Web peut accéder à des informations à partir d’Internet (telles que des documents HTML ou actifs) ou un intranet, ainsi que des dossiers dans le système de fichiers local et sur un réseau. En dérivant la classe d’affichage de l’application de [CHtmlView](../../mfc/reference/chtmlview-class.md), vous faites de l’application un navigateur Web en fournissant la vue avec le contrôle WebBrowser.

## <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Pour créer une application de navigateur Web basée sur l’architecture document/vue MFC

1. Suivez les instructions de [création d’une application MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Dans la page type d' [application](../../mfc/reference/application-type-mfc-application-wizard.md) de l’Assistant Application MFC, assurez-vous que la zone **architecture document/vue** est sélectionnée. (Vous pouvez choisir un **seul document** ou **plusieurs documents**, mais pas les **boîtes de dialogue**.)

1. Dans la page [vérifier les classes générées](../../mfc/reference/generated-classes-mfc-application-wizard.md) , utilisez le menu déroulant **classe de Base** pour sélectionner `CHtmlView`.

1. Sélectionnez les autres options que vous souhaitez intégrer à l’application squelette.

1. Cliquez sur **Terminer**.

Le contrôle WebBrowser prend en charge la navigation Web via les liens hypertexte et la navigation Uniform Resource Locator (URL). Le contrôle gère une liste d’historique qui permet à l’utilisateur de naviguer vers l’avant et vers l’arrière dans les sites, dossiers et documents précédemment parcourus. Le contrôle gère directement la navigation, les liens hypertexte, les listes d’historique, les favoris et la sécurité. Les applications peuvent utiliser le contrôle WebBrowser comme conteneur de documents actifs pour héberger également des documents actifs. Par conséquent, les documents mis en forme de manière enrichie, tels que les feuilles de calcul Microsoft Excel ou les documents Word, peuvent être ouverts et modifiés sur place à partir du contrôle WebBrowser. Le contrôle WebBrowser est également un conteneur de contrôles ActiveX qui peut héberger n’importe quel contrôle ActiveX.

> [!NOTE]
> Le contrôle ActiveX WebBrowser (et par conséquent `CHtmlView`) est disponible uniquement pour les applications qui s’exécutent sous les versions de Windows dans lesquelles Internet Explorer 4,0 ou version ultérieure a été installé.

Étant donné que `CHtmlView` implémente simplement le contrôle de navigateur Web Microsoft, sa prise en charge de l’impression n’est pas similaire à celle des autres classes dérivées de [CView](../../mfc/reference/cview-class.md). Au lieu de cela, le contrôle WebBrowser implémente l’interface utilisateur de l’imprimante et l’impression. Par conséquent, `CHtmlView` ne prend pas en charge l’aperçu avant impression et l’infrastructure ne fournit pas d’autres fonctions de prise en charge de l’impression : par exemple, [CView :: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView :: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)et [CView :: OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), qui sont disponibles dans d’autres applications MFC.

`CHtmlView` agit comme un wrapper pour le contrôle de navigateur Web, qui donne à votre application une vue sur une page Web ou une page HTML. L’Assistant crée un remplacement dans la fonction [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) de la classe d’affichage, en fournissant un lien de navigation vers le site C++ Web Microsoft Visual :

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

Vous pouvez remplacer ce site par l’un de vos propres sites, ou vous pouvez utiliser la fonction membre [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) pour ouvrir une page HTML qui réside dans le script de ressources du projet en tant que contenu par défaut pour la vue. Par exemple :

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>Voir aussi

[Exemple de MFCIE MFC](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet)<br/>
[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Définir des propriétés de build et de compilateur](../../build/working-with-project-properties.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)<br/>
[Définir des propriétés de build et de compilateur](../../build/working-with-project-properties.md)
