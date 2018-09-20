---
title: 'TN071 : Implémentation IOleCommandTarget MFC | Microsoft Docs'
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
ms.openlocfilehash: 6d8d4b0f740e69b57944cb35f2213ae0fd54b511
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386286"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071 : Implémentation IOleCommandTarget MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Le `IOleCommandTarget` interface permet les objets et leurs conteneurs à répartir les uns des autres commandes. Par exemple, barres d’outils d’un objet peuvent contenir des boutons pour les commandes telles que `Print`, `Print Preview`, `Save`, `New`, et `Zoom`. Si un tel objet ont été incorporées dans un conteneur qui prend en charge `IOleCommandTarget`, l’objet pouvant permettre de ses boutons et transférer les commandes pour le conteneur pour le traitement lorsque l’utilisateur a cliqué sur eux. Si un conteneur voulu l’objet incorporé s’imprimer, il peut effectuer cette demande en envoyant une commande via le `IOleCommandTarget` interface de l’objet incorporé.

`IOleCommandTarget` est une interface similaire à Automation, car il est utilisé par un client pour appeler des méthodes sur un serveur. Toutefois, à l’aide de `IOleCommandTarget` économise la surcharge des appels via les interfaces d’automatisation, car les programmeurs n’êtes pas obligé d’utiliser généralement coûteux `Invoke` méthode de `IDispatch`.

Dans MFC, la `IOleCommandTarget` interface est utilisée par les serveurs de documents actifs pour permettre aux conteneurs de documents actifs distribuer des commandes sur le serveur. La classe de serveur de documents actifs, `CDocObjectServerItem`, utilise des tables d’interface MFC (consultez [TN038 : implémentation IUnknown MFC/OLE](../mfc/tn038-mfc-ole-iunknown-implementation.md)) pour implémenter le `IOleCommandTarget` interface.

`IOleCommandTarget` est également implémentée dans le `COleFrameHook` classe. `COleFrameHook` est une classe MFC non documentée qui implémente les fonctionnalités de la fenêtre frame de conteneurs de modifications sur place. `COleFrameHook` utilise également des mappages d’interface MFC pour implémenter le `IOleCommandTarget` interface. `COleFrameHook`d’implémentation de `IOleCommandTarget` transfère des commandes OLE pour `COleDocObjectItem`-dérivée des conteneurs de documents actifs. Cela permet à n’importe quel conteneur de document MFC Active recevoir des messages à partir de serveurs de relation contenant-contenu de document actif.

## <a name="mfc-ole-command-maps"></a>Mappages de commande OLE MFC

Les développeurs MFC peuvent tirer parti de `IOleCommandTarget` à l’aide de OLE MFC commande maps. Mappages de commande OLE sont comme des tables des messages, car ils peuvent être utilisés pour mapper les commandes OLE aux fonctions membres de la classe qui contient le mappage de la commande. Pour que cela fonctionne, placer des macros dans le mappage de commande pour spécifier le groupe de commandes OLE de la commande que vous souhaitez gérer, de la commande OLE et de l’ID de commande de la [WM_COMMAND](/windows/desktop/menurc/wm-command) message qui sera envoyée lors de la réception de la commande OLE. MFC fournit également plusieurs des macros prédéfinies pour les commandes OLE standard. Pour obtenir la liste de l’OLE standard les commandes qui ont été conçus pour utiliser avec les applications Microsoft Office, consultez l’énumération OLECMDID, qui est définie dans docobj.h.

Lorsqu’une commande OLE est reçue par une application MFC qui contient une table de commandes OLE, MFC tente de trouver l’ID de commande et le groupe de commandes pour la commande demandée dans le mappage de commande OLE de l’application. Si une correspondance est trouvée, un message WM_COMMAND est distribué à l’application contenant le mappage de la commande avec l’ID de la commande demandée. (Consultez la description de `ON_OLECMD` ci-dessous.) De cette façon, les commandes OLE distribués à une application sont transformées en messages WM_COMMAND par MFC. Les messages WM_COMMAND sont ensuite acheminés via les tables de messages de l’application à l’aide de la norme MFC [routage des commandes](../mfc/command-routing.md) architecture.

Contrairement aux tables des messages, mappages de commande OLE MFC ne sont pas pris en charge par ClassWizard. Les développeurs MFC doivent ajouter manuellement les entrées de mappage de commande OLE et de prise en charge des cartes de commande OLE. Commande OLE mappages peuvent être ajoutés à des serveurs de documents actifs MFC dans n’importe quelle classe qui se trouve dans la chaîne de routage des messages WM_COMMAND au moment où le document actif est actif en place dans un conteneur. Ces classes incluent les classes dérivées de l’application [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), et [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). Conteneurs de documents actifs, les mappages de commande OLE peuvent uniquement être ajoutées à la [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-classe dérivée. En outre, dans des conteneurs de documents actifs, les messages WM_COMMAND sont uniquement envoyés à la table des messages dans la `COleDocObjectItem`-classe dérivée.

## <a name="ole-command-map-macros"></a>Macros de table de commande OLE

Pour ajouter des fonctionnalités de mappage de commande à votre classe, utilisez les macros suivantes :

```cpp
DECLARE_OLECMD_MAP ()
```

Cette macro est envoyé dans la déclaration de classe (généralement dans le fichier d’en-tête) de la classe qui contient le mappage de la commande.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
Nom de la classe qui contient le mappage de la commande.

*classe de base*<br/>
Nom de la classe de base de la classe qui contient le mappage de la commande.

Cette macro marque le début de la carte de la commande. Utilisez cette macro dans le fichier d’implémentation pour la classe qui contient le mappage de la commande.

```
END_OLECMD_MAP()
```

Cette macro marque la fin de la carte de la commande. Utilisez cette macro dans le fichier d’implémentation pour la classe qui contient le mappage de la commande. Cette macro doit suivre toujours la macro BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Pointeur vers le GUID de groupe de commandes de la commande OLE. Ce paramètre est **NULL** pour le groupe de commandes OLE standard.

*olecmdid*<br/>
ID de commande OLE de la commande à appeler.

*ID*<br/>
ID du message WM_COMMAND à envoyer à l’application contenant le mappage de la commande lors de cette commande OLE est appelée.

Utiliser l’on_olecmd (macro) dans le mappage de commande pour ajouter des entrées pour les commandes OLE que vous souhaitez gérer. Lorsque les commandes OLE sont reçus, ils seront convertis au message WM_COMMAND spécifié et acheminés via le mappage de message de l’application à l’aide de l’architecture de routage des commandes MFC standard.

## <a name="example"></a>Exemple

L’exemple suivant montre comment ajouter la fonctionnalité de gestion de commande OLE à un serveur de document actif de MFC pour gérer le [OLECMDID_PRINT](/windows/desktop/api/docobj/ne-docobj-olecmdid) commande OLE. Cet exemple suppose que vous avez utilisé par AppWizard pour générer une application MFC qui est un serveur de document actif.

1. Dans votre `CView`-dérivés d’en-tête de la classe, ajoutez la macro DECLARE_OLECMD_MAP à la déclaration de classe.

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

2. Dans le fichier d’implémentation pour le `CView`-classe dérivée, ajoutez les macros BEGIN_OLECMD_MAP et END_OLECMD_MAP :

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Pour gérer la commande d’impression OLE standard, ajoutez un [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) macro pour le mappage de la commande en spécifiant l’ID de commande OLE pour la commande d’impression standard et **ID_FILE_PRINT** pour l’ID de WM_COMMAND. **ID_FILE_PRINT** est la norme commande d’impression ID utilisée par les applications MFC générées par AppWizard :

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Notez qu’une des macros de commande standards OLE, définies dans afxdocob.h, peut être utilisée à la place l’on_olecmd (macro), car **OLECMDID_PRINT** est un ID de commande OLE standard. L’on_olecmd_print (macro) exécutera la même tâche que l’on_olecmd (macro) ci-dessus.

Lorsqu’une application conteneur envoie ce serveur un **OLECMDID_PRINT** commande par le biais du serveur `IOleCommandTarget` interface, la bibliothèque MFC l’impression du Gestionnaire de commandes est invoqué dans le serveur, le serveur à l’application d’impression. Code du conteneur de documents actifs pour appeler la commande d’impression ajoutée aux étapes ci-dessus ressemblent à ceci :

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
