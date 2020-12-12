---
description: 'En savoir plus sur : TN071 : implémentation IOleCommandTarget MFC'
title: 'TN071 : Implémentation IOleCommandTarget MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 190dd64f6fd14d6231a6870bf6697a9a85182166
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214505"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071 : Implémentation IOleCommandTarget MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

L' `IOleCommandTarget` interface permet aux objets et à leurs conteneurs de distribuer les commandes les unes aux autres. Par exemple, les barres d’outils d’un objet peuvent contenir des boutons pour les commandes telles que,,, `Print` `Print Preview` `Save` `New` et `Zoom` . Si un objet de ce type a été incorporé dans un conteneur qui prend en charge `IOleCommandTarget` , l’objet peut activer ses boutons et transférer les commandes au conteneur pour traitement lorsque l’utilisateur clique dessus. Si un conteneur souhaite que l’objet incorporé s’imprime lui-même, il peut effectuer cette requête en envoyant une commande par le biais `IOleCommandTarget` de l’interface de l’objet incorporé.

`IOleCommandTarget` est une interface de type Automation en ce qu’elle est utilisée par un client pour appeler des méthodes sur un serveur. Toutefois, l’utilisation `IOleCommandTarget` de économise la surcharge liée à l’exécution d’appels via des interfaces d’automatisation, car les programmeurs n’ont pas besoin d’utiliser la méthode généralement coûteuse `Invoke` de `IDispatch` .

Dans MFC, l' `IOleCommandTarget` interface est utilisée par les serveurs de documents actifs pour permettre aux conteneurs de documents actifs de distribuer des commandes au serveur. La classe du serveur de documents actifs, `CDocObjectServerItem` , utilise des mappages d’interface MFC (consultez [TN038 : implémentation IUnknown MFC/OLE](../mfc/tn038-mfc-ole-iunknown-implementation.md)) pour implémenter l' `IOleCommandTarget` interface.

`IOleCommandTarget` est également implémentée dans la `COleFrameHook` classe. `COleFrameHook` est une classe MFC non documentée qui implémente la fonctionnalité de fenêtre frame des conteneurs d’édition sur place. `COleFrameHook` utilise également des mappages d’interface MFC pour implémenter l' `IOleCommandTarget` interface. `COleFrameHook`l’implémentation de `IOleCommandTarget` transfère des commandes OLE à `COleDocObjectItem` des conteneurs de documents actifs dérivés. Cela permet à n’importe quel conteneur de documents actifs MFC de recevoir des messages à partir de serveurs de documents actifs contenus.

## <a name="mfc-ole-command-maps"></a>Mappages de commandes OLE MFC

Les développeurs MFC peuvent tirer parti de `IOleCommandTarget` à l’aide des mappages de commandes OLE MFC. Les mappages de commandes OLE sont similaires aux tables des messages, car ils peuvent être utilisés pour mapper des commandes OLE aux fonctions membres de la classe qui contient le mappage de commandes. Pour ce faire, placez les macros dans le mappage de commandes afin de spécifier le groupe de commandes OLE de la commande que vous souhaitez gérer, la commande OLE et l’ID de commande du [WM_COMMAND](/windows/win32/menurc/wm-command) message qui sera envoyé lors de la réception de la commande OLE. MFC fournit également un certain nombre de macros prédéfinies pour les commandes OLE standard. Pour obtenir la liste des commandes OLE standard qui ont été conçues à l’origine pour une utilisation avec les applications Microsoft Office, consultez l’énumération OLECMDID, qui est définie dans docobj. h.

Quand une commande OLE est reçue par une application MFC qui contient un mappage de commandes OLE, MFC tente de trouver l’ID de commande et le groupe de commandes pour la commande demandée dans le mappage de commandes OLE de l’application. Si une correspondance est trouvée, un message de WM_COMMAND est distribué à l’application contenant le mappage de commande avec l’ID de la commande demandée. (Voir la description `ON_OLECMD` ci-dessous.) De cette façon, les commandes OLE distribuées à une application sont transformées en WM_COMMAND messages par MFC. Les messages WM_COMMAND sont ensuite routés via les tables des messages de l’application à l’aide de l’architecture de [routage des commandes](../mfc/command-routing.md) standard MFC.

Contrairement aux tables de messages, les mappages de commandes OLE MFC ne sont pas pris en charge par ClassWizard. Les développeurs MFC doivent ajouter manuellement la prise en charge des mappages de commandes OLE et les entrées de mappage de commandes OLE. Les mappages de commandes OLE peuvent être ajoutés aux serveurs de documents actifs MFC dans toutes les classes qui se trouvent dans le WM_COMMAND chaîne de routage des messages au moment où le document actif est actif sur place dans un conteneur. Ces classes incluent les classes de l’application dérivées de [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md)et [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). Dans les conteneurs de documents actifs, les mappages de commandes OLE peuvent uniquement être ajoutés à la classe dérivée de [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md). En outre, dans les conteneurs de documents actifs, les messages de WM_COMMAND sont envoyés uniquement à la table des messages de la `COleDocObjectItem` classe dérivée de.

## <a name="ole-command-map-macros"></a>Macros de mappage de commandes OLE

Utilisez les macros suivantes pour ajouter la fonctionnalité de mappage de commande à votre classe :

```cpp
DECLARE_OLECMD_MAP ()
```

Cette macro est insérée dans la déclaration de classe (généralement dans le fichier d’en-tête) de la classe qui contient le mappage de commandes.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*Les*<br/>
Nom de la classe qui contient le mappage de commandes.

*baseClass*<br/>
Nom de la classe de base de la classe qui contient le mappage de commandes.

Cette macro marque le début du mappage de commandes. Utilisez cette macro dans le fichier d’implémentation pour la classe qui contient le mappage de commandes.

```
END_OLECMD_MAP()
```

Cette macro marque la fin du mappage de commandes. Utilisez cette macro dans le fichier d’implémentation pour la classe qui contient le mappage de commandes. Cette macro doit toujours suivre la macro BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Pointeur vers le GUID du groupe de commandes de la commande OLE. Ce paramètre a la **valeur null** pour le groupe de commandes OLE standard.

*olecmdid*<br/>
ID de commande OLE de la commande à appeler.

*id*<br/>
ID du message WM_COMMAND à envoyer à l’application contenant le mappage de commandes lorsque cette commande OLE est appelée.

Utilisez la macro ON_OLECMD dans le mappage de commandes pour ajouter des entrées pour les commandes OLE que vous souhaitez gérer. Une fois les commandes OLE reçues, elles sont converties dans le message de WM_COMMAND spécifié et acheminées via la table des messages de l’application à l’aide de l’architecture de routage de commande MFC standard.

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter la fonctionnalité de gestion de commandes OLE à un serveur de documents actifs MFC pour gérer la commande OLE [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) . Cet exemple suppose que vous avez utilisé AppWizard pour générer une application MFC qui est un serveur de documents actifs.

1. Dans le `CView` fichier d’en-tête de votre classe dérivée de, ajoutez la macro DECLARE_OLECMD_MAP à la déclaration de classe.

    > [!NOTE]
    > Utilisez la `CView` classe dérivée de, car il s’agit de l’une des classes du serveur de documents actif qui se trouve dans le WM_COMMAND chaîne de routage des messages.

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. Dans le fichier d’implémentation de la `CView` classe dérivée de, ajoutez les macros BEGIN_OLECMD_MAP et END_OLECMD_MAP :

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Pour gérer la commande OLE Print standard, ajoutez une macro [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) au mappage de commandes en spécifiant l’ID de commande OLE pour la commande d’impression standard et **ID_FILE_PRINT** pour l’ID de WM_COMMAND. **ID_FILE_PRINT** est l’ID de commande d’impression standard utilisé par les applications MFC générées par AppWizard :

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Notez que l’une des macros de commande OLE standard, définie dans AfxDocOb. h, peut être utilisée à la place de la macro ON_OLECMD, car **OLECMDID_PRINT** est un ID de commande OLE standard. La macro ON_OLECMD_PRINT effectue la même tâche que la macro ON_OLECMD présentée ci-dessus.

Quand une application de conteneur envoie ce serveur à une commande **OLECMDID_PRINT** via l' `IOleCommandTarget` interface du serveur, le gestionnaire de commandes d’impression MFC est appelé sur le serveur, ce qui entraîne l’impression de l’application par le serveur. Le code du conteneur de documents actifs permettant d’appeler la commande Imprimer ajoutée dans les étapes ci-dessus ressemble à ce qui suit :

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
