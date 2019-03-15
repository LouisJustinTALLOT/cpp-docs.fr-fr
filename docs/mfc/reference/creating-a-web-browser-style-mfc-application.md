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
ms.openlocfilehash: 12df36188bd858f73ff4834236a19583023e5f93
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57809871"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Création d'une application MFC de style navigateur Web

Une application de style navigateur Web peut accéder aux informations à partir d’Internet (tels que HTML ou documents actifs) ou un intranet, ainsi que les dossiers du système de fichiers local et sur un réseau. En dérivant la classe d’affichage de l’application de [CHtmlView](../../mfc/reference/chtmlview-class.md)efficace vous rendre à l’application un navigateur Web en fournissant la vue avec le contrôle WebBrowser.

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Pour créer une application de navigateur Web basée sur l’architecture document/vue MFC

1. Suivez les instructions de [création d’une Application MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Dans l’Assistant Application MFC [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page, assurez-vous que le **architecture Document/vue** est activée. (Vous pouvez choisir une **monodocument** ou **plusieurs documents**, mais pas **basée sur un dialogue**.)

1. Sur le [Classes générées](../../mfc/reference/generated-classes-mfc-application-wizard.md) page, utilisez la **classe de Base** menu déroulant pour sélectionner `CHtmlView`.

1. Sélectionnez d’autres options intégrées à l’application squelette.

1. Cliquez sur **Terminer**.

Le contrôle WebBrowser prend en charge la navigation sur le Web par le biais des liens hypertexte et de navigation de Uniform Resource Locator (URL). Le contrôle conserve un historique qui lui permet de naviguer en avant et arrière dans déjà consultées sites, des dossiers et des documents. Le contrôle gère directement la navigation, les liens hypertexte, les listes d’historique, Favoris et sécurité. Applications peuvent utiliser le contrôle WebBrowser en tant que conteneur de documents actifs pour héberger également des documents active. Par conséquent, mise en forme enrichie des documents tels que des feuilles de calcul Microsoft Excel ou des documents Word peuvent être ouvert et modifiés sur place à partir du contrôle WebBrowser. Le contrôle WebBrowser est également un conteneur de contrôles ActiveX qui peut héberger n’importe quel contrôle ActiveX.

> [!NOTE]
>  Le contrôle WebBrowser ActiveX (et par conséquent `CHtmlView`) est disponible uniquement pour les applications qui s’exécutent sous des versions de Windows dans Internet Explorer 4.0 ou version ultérieure a été installé.

Étant donné que `CHtmlView` implémente simplement le contrôle de navigateur Web Microsoft, sa prise en charge pour l’impression n’est pas comme les autres [CView](../../mfc/reference/cview-class.md)-classes dérivées. Au lieu de cela, le contrôle WebBrowser implémente l’interface utilisateur de l’imprimante et l’impression. Par conséquent, `CHtmlView` est pas prise en charge l’aperçu avant impression, et le framework ne fournit pas d’autres fonctions de prise en charge l’impression : par exemple, [comme CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), et [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), qui sont disponibles dans d’autres applications MFC.

`CHtmlView` sert de wrapper pour le contrôle de navigateur Web, ce qui donne une vue sur un site Web ou une page HTML à votre application. L’Assistant crée une substitution de la [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) fonction dans la classe d’affichage, en fournissant un lien de navigation vers le site Web de Microsoft Visual C++ :

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

Vous pouvez remplacer ce site par un des vôtres, ou vous pouvez utiliser la [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) fonction membre pour ouvrir une page HTML qui réside dans le script de ressources du projet en tant que le contenu par défaut pour la vue. Exemple :

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

[MFC, exemple MFCIE](https://github.com/Microsoft/VCSamples)<br/>
[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Définir un compilateur et les propriétés de build](../../build/working-with-project-properties.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)<br/>
[Définir un compilateur et les propriétés de build](../../build/working-with-project-properties.md)

