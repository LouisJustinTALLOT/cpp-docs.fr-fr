---
title: 'TN071 : Implémentation IOleCommandTarget MFC | Documents Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebd796690407fe0e65bc790c52477c7e4d149250
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122619"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071 : Implémentation IOleCommandTarget MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Le `IOleCommandTarget` interface permet les objets et leurs conteneurs expédition des commandes à l’autre. Par exemple, barres d’outils d’un objet peuvent contenir des boutons pour les commandes telles que `Print`, `Print Preview`, `Save`, `New`, et `Zoom`. Si un tel objet ont été incorporés dans un conteneur qui prend en charge `IOleCommandTarget`, l’objet peut activer des boutons et transférer les commandes pour le conteneur pour le traitement lorsque l’utilisateur a cliqué sur les. Si un conteneur souhaitiez l’objet incorporé s’imprime, il peut effectuer cette demande en envoyant une commande via le `IOleCommandTarget` interface de l’objet incorporé.

`IOleCommandTarget` est une interface d’automatisation de type, car il est utilisé par un client pour appeler des méthodes sur un serveur. Toutefois, à l’aide de `IOleCommandTarget` enregistre la surcharge des appels via les interfaces Automation, car les programmeurs n’êtes pas obligé d’utiliser le généralement coûteuses `Invoke` méthode `IDispatch`.

Dans MFC, la `IOleCommandTarget` interface est utilisée par les serveurs de documents actifs pour autoriser les conteneurs de documents actifs distribuer des commandes sur le serveur. La classe de serveur de document actif, `CDocObjectServerItem`, utilise les mappages d’interface MFC (consultez [TN038 : implémentation IUnknown MFC/OLE](../mfc/tn038-mfc-ole-iunknown-implementation.md)) pour implémenter le `IOleCommandTarget` interface.

`IOleCommandTarget` est également implémentée dans le `COleFrameHook` classe. `COleFrameHook` est une classe MFC non documentée qui implémente les fonctionnalités de la fenêtre frame de conteneurs de modification sur place. `COleFrameHook` utilise également les mappages d’interface MFC pour implémenter le `IOleCommandTarget` interface. `COleFrameHook`de la mise en œuvre de `IOleCommandTarget` transfère des commandes OLE pour `COleDocObjectItem`-dérivées des conteneurs de documents actifs. Cela permet à n’importe quel conteneur de documents actifs MFC recevoir des messages à partir de serveurs de document actif contenu.

## <a name="mfc-ole-command-maps"></a>Mappages de commande OLE MFC

Les développeurs MFC peuvent tirer parti de `IOleCommandTarget` à l’aide de OLE MFC commande maps. Mappages de commande OLE sont comme des tables des messages car ils peuvent être utilisés pour mapper les commandes OLE aux fonctions membres de la classe qui contient le mappage de la commande. Pour ce faire, placer des macros dans le mappage de commande pour spécifier le groupe de commandes OLE de la commande que vous souhaitez gérer, de la commande OLE et de l’ID de commande de la [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) message qui sera envoyée lors de la réception de la commande OLE. MFC fournit également plusieurs des macros prédéfinies pour les commandes OLE standard. Pour obtenir la liste de l’OLE standard les commandes qui ont été conçus pour utiliser avec les applications Microsoft Office, consultez l’énumération OLECMDID, qui est définie dans docobj.h.

Lorsqu’une commande OLE est reçue par une application MFC qui contient une table de commandes OLE, MFC tente de trouver l’ID de commande et le groupe de commandes pour la commande demandée dans le mappage de commande OLE de l’application. Si une correspondance est trouvée, un message WM_COMMAND est distribué à l’application contenant le mappage de commande avec l’ID de la commande demandée. (Consultez la description de `ON_OLECMD` ci-dessous.) De cette façon, les commandes OLE distribués à une application sont activées dans WM_COMMAND (messages) par MFC. Les messages WM_COMMAND sont ensuite routés via des tables des messages de l’application à l’aide de la norme MFC [routage des commandes](../mfc/command-routing.md) architecture.

Contrairement aux tables des messages, mappages de commande OLE MFC ne sont pas pris en charge par ClassWizard. Les développeurs MFC doivent ajouter manuellement les entrées de mappage de commande OLE et de la prise en charge des cartes de commande OLE. Commande OLE mappages peuvent être ajoutés à des serveurs de documents actifs MFC dans n’importe quelle classe qui se trouve dans la chaîne de routage des messages WM_COMMAND au moment où le document actif est actif en place dans un conteneur. Ces classes incluent les classes dérivées de l’application [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), et [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). Dans les conteneurs de documents actifs, les mappages de commande OLE ne peuvent être ajoutés à la [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-classe dérivée. En outre, dans les conteneurs de documents actifs, les messages WM_COMMAND seront uniquement envoyés à la table des messages dans la `COleDocObjectItem`-classe dérivée.

## <a name="ole-command-map-macros"></a>Macros de table de commande OLE

Pour ajouter des fonctionnalités de mappage de commande à votre classe, utilisez les macros suivantes :

```cpp
DECLARE_OLECMD_MAP ()
```

Cette macro est placé dans la déclaration de classe (généralement dans le fichier d’en-tête) de la classe qui contient le mappage de la commande.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*  
 Nom de la classe qui contient le mappage de la commande.

*baseClass*  
 Nom de la classe de base de la classe qui contient le mappage de la commande.

Cette macro marque le début de la carte de la commande. Utilisez cette macro dans le fichier d’implémentation pour la classe qui contient le mappage de la commande.

```
END_OLECMD_MAP()
```

Cette macro marque la fin de la table de commande. Utilisez cette macro dans le fichier d’implémentation pour la classe qui contient le mappage de la commande. Cette macro doit suivre toujours la macro BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*  
 Pointeur vers le GUID du groupe de commandes de la commande OLE. Ce paramètre est **NULL** pour le groupe de commandes OLE standard.

*olecmdid*  
 ID de commande OLE de la commande à appeler.

*ID*  
 ID du message WM_COMMAND à envoyer à l’application contenant le mappage de commande lorsque cette commande OLE est appelée.

Utiliser la macro ON_OLECMD dans le mappage de commande pour ajouter des entrées pour les commandes OLE que vous souhaitez gérer. Lorsque les commandes OLE sont reçus, elles seront converties en message WM_COMMAND spécifié et routés via le mappage de message de l’application à l’aide de l’architecture de routage des commandes MFC standard.

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter des capacités de gestion de commande OLE à un serveur de documents actifs MFC pour gérer les [OLECMDID_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) commande OLE. Cet exemple suppose que vous avez utilisé par AppWizard pour générer une application MFC qui est un serveur de document actif.

1. Dans votre `CView`-dérivée d’en-tête de la classe, ajoutez la macro DECLARE_OLECMD_MAP à la déclaration de classe.

    > [!NOTE]
    > Utilisez le `CView`-classe dérivée, car il est une des classes dans le serveur de document actif qui se trouve dans la chaîne de routage des messages WM_COMMAND.

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

2. Dans le fichier d’implémentation pour la `CView`-classe dérivée, ajoutez les macros BEGIN_OLECMD_MAP et END_OLECMD_MAP :

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Pour gérer la commande d’impression OLE standard, ajoutez un [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) macro pour le mappage de commande en spécifiant l’ID de commande OLE de la commande d’impression standard et **ID_FILE_PRINT** pour l’ID de WM_COMMAND. **ID_FILE_PRINT** est la norme d’ID de commande d’impression utilisé par les applications générées par AppWizard MFC :

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Notez que parmi les macros de commande OLE standards, définis dans afxdocob.h, peut être utilisé à la place de la macro ON_OLECMD car **OLECMDID_PRINT** est un ID de commande OLE standard. La macro ON_OLECMD_PRINT sera accomplir la même tâche que la macro ON_OLECMD ci-dessus.

Lorsqu’une application conteneur envoie ce serveur un **OLECMDID_PRINT** commande par le biais du serveur `IOleCommandTarget` interface, la bibliothèque MFC l’impression du Gestionnaire de commandes sera appelé sur le serveur, par le serveur d’impression de l’application. Code du conteneur de documents actifs pour appeler la commande d’impression ajoutée dans les étapes ci-dessus ressemblerait à ceci :

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

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)  
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)  
