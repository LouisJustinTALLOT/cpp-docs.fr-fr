---
title: 'TN006 : tables des messages'
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
ms.openlocfilehash: 6b387b851f5a76cd0d11957a87e57307d624759e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228529"
---
# <a name="tn006-message-maps"></a>TN006 : tables des messages

Cette note décrit la fonctionnalité de table des messages MFC.

## <a name="the-problem"></a>Le problème

Microsoft Windows implémente des fonctions virtuelles dans les classes de fenêtre qui utilisent sa fonctionnalité de messagerie. En raison du grand nombre de messages impliqués, le fait de fournir une fonction virtuelle distincte pour chaque message Windows crée un vtable à grande échelle.

Étant donné que le nombre de messages Windows définis par le système change au fil du temps, et parce que les applications peuvent définir leurs propres messages Windows, les tables des messages fournissent un niveau d’indirection qui empêche les modifications de l’interface d’altérer le code existant.

## <a name="overview"></a>Vue d’ensemble

MFC fournit une alternative à l’instruction switch qui a été utilisée dans les programmes Windows traditionnels pour gérer les messages envoyés à une fenêtre. Un mappage des messages aux méthodes peut être défini de sorte que lorsqu’un message est reçu par une fenêtre, la méthode appropriée est appelée automatiquement. Cette fonctionnalité de table des messages est conçue pour ressembler à des fonctions virtuelles, mais elle n’a pas d’avantages supplémentaires avec les fonctions virtuelles C++.

## <a name="defining-a-message-map"></a>Définition d’une table des messages

La macro [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) déclare trois membres pour une classe.

- Tableau privé d’entrées de AFX_MSGMAP_ENTRY appelées *_messageEntries*.

- Une structure AFX_MSGMAP protégée appelée *messageMap* qui pointe vers le tableau *_messageEntries* .

- Une fonction virtuelle protégée appelée `GetMessageMap` qui retourne l’adresse de *messageMap*.

Cette macro doit être placée dans la déclaration de toute classe utilisant des tables de messages. Par Convention, il se trouve à la fin de la déclaration de classe. Par exemple :

```cpp
class CMyWnd : public CMyParentWndClass
{
    // my stuff...

protected:
    //{{AFX_MSG(CMyWnd)
    afx_msg void OnPaint();
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};
```

Il s’agit du format généré par AppWizard et ClassWizard lorsqu’ils créent des classes. Les crochets//{{et//}} sont nécessaires pour ClassWizard.

La table de la table des messages est définie à l’aide d’un ensemble de macros qui se développent en entrées de la table des messages. Une table commence par un appel de macro [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) , qui définit la classe gérée par cette table des messages et la classe parente à laquelle les messages non gérés sont passés. La table se termine par l’appel de macro [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) .

Entre ces deux appels de macro est une entrée pour chaque message à gérer par cette table des messages. Chaque message Windows standard a une macro de la forme ON_WM_*MESSAGE_NAME* qui génère une entrée pour ce message.

Une signature de fonction standard a été définie pour décompresser les paramètres de chaque message Windows et fournir la sécurité de type. Ces signatures peuvent se trouver dans le fichier AFXWIN. h dans la déclaration de [CWnd](../mfc/reference/cwnd-class.md). Chacune d’elles est marquée avec le mot clé **afx_msg** pour faciliter l’identification.

> [!NOTE]
> ClassWizard requiert que vous utilisiez le mot clé **afx_msg** dans les déclarations de votre gestionnaire de table des messages.

Ces signatures de fonction ont été dérivées à l’aide d’une convention simple. Le nom de la fonction commence toujours par `"On` «. Elle est suivie du nom du message Windows avec le « WM_ » supprimé et la première lettre de chaque mot en majuscule. L’ordre des paramètres est *wParam* suivi de `LOWORD` (*lParam*) Then `HIWORD` (*lParam*). Les paramètres inutilisés ne sont pas transmis. Tous les descripteurs encapsulés par les classes MFC sont convertis en pointeurs vers les objets MFC appropriés. L’exemple suivant montre comment gérer le message WM_PAINT et provoquer l' `CMyWnd::OnPaint` appel de la fonction :

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

La table des messages doit être définie à l’extérieur de la portée de toute définition de fonction ou de classe. Il ne doit pas être placé dans un bloc extern "C".

> [!NOTE]
> ClassWizard modifiera les entrées de la table des messages qui se produisent entre le crochet de commentaires//{{et//}}.

## <a name="user-defined-windows-messages"></a>Messages Windows définis par l’utilisateur

Les messages définis par l’utilisateur peuvent être inclus dans une table des messages à l’aide de la macro [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) . Cette macro accepte un numéro de message et une méthode sous la forme :

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

Dans cet exemple, nous créons un gestionnaire pour un message personnalisé dont l’ID de message Windows est dérivé de la base standard WM_USER pour les messages définis par l’utilisateur. L’exemple suivant montre comment appeler ce gestionnaire :

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

La plage de messages définis par l’utilisateur qui utilisent cette approche doit être comprise dans la plage WM_USER 0x7FFF.

> [!NOTE]
> ClassWizard ne prend pas en charge l’entrée de routines de gestionnaire ON_MESSAGE à partir de l’interface utilisateur ClassWizard. Vous devez les entrer manuellement à partir de l’éditeur de Visual C++. ClassWizard analyse ces entrées et vous permet de les parcourir comme n’importe quelle autre entrée de table des messages.

## <a name="registered-windows-messages"></a>Messages Windows inscrits

La fonction [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) est utilisée pour définir un nouveau message de fenêtre dont l’unicité est garantie dans tout le système. La macro ON_REGISTERED_MESSAGE est utilisée pour gérer ces messages. Cette macro accepte le nom d’une variable *uint near* qui contient l’ID de message Windows enregistré. Par exemple

```cpp
class CMyWnd : public CMyParentWndClass
{
public:
    CMyWnd();

    //{{AFX_MSG(CMyWnd)
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};

static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

La variable d’ID de message Windows inscrite (WM_FIND dans cet exemple) doit être une variable *proche* en raison de la façon dont ON_REGISTERED_MESSAGE est implémentée.

La plage de messages définis par l’utilisateur qui utilisent cette approche sera comprise entre 0xC000 et 0xFFFF.

> [!NOTE]
> ClassWizard ne prend pas en charge l’entrée de routines de gestionnaire ON_REGISTERED_MESSAGE à partir de l’interface utilisateur ClassWizard. Vous devez les entrer manuellement dans l’éditeur de texte. ClassWizard analyse ces entrées et vous permet de les parcourir comme n’importe quelle autre entrée de table des messages.

## <a name="command-messages"></a>Messages de commande

Les messages de commande des menus et des accélérateurs sont gérés dans les tables des messages avec la macro ON_COMMAND. Cette macro accepte un ID de commande et une méthode. Seul le message WM_COMMAND spécifique qui a un *wParam* égal à l’ID de commande spécifié est géré par la méthode spécifiée dans l’entrée de la table des messages. Les fonctions membres du gestionnaire de commandes ne prennent aucun paramètre et retournent **`void`** . La macro se présente sous la forme suivante :

```cpp
ON_COMMAND(id, memberFxn)
```

Les messages de mise à jour de commande sont routés via le même mécanisme, mais utilisent la macro ON_UPDATE_COMMAND_UI à la place. Les fonctions membres du gestionnaire de mise à jour de commandes acceptent un seul paramètre, un pointeur vers un objet [CCmdUI](../mfc/reference/ccmdui-class.md) et retournent **`void`** . La macro se présente sous la forme

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Les utilisateurs expérimentés peuvent utiliser la macro ON_COMMAND_EX, qui est une forme étendue de gestionnaires de messages de commande. La macro fournit un sur-ensemble de la fonctionnalité ON_COMMAND. Les fonctions membres du gestionnaire de commandes étendues acceptent un seul paramètre, un **uint** qui contient l’ID de commande et retournent une valeur **booléenne**. La valeur de retour doit être **true** pour indiquer que la commande a été gérée. Sinon, le routage continue vers d’autres objets de la cible de commande.

Exemples de ces formes :

- Dans Resource. h (généralement généré par Visual C++)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- À l’intérieur de la déclaration de classe

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- À l’intérieur de la définition de la table des messages

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- Dans le fichier d’implémentation

    ```cpp
    void CMyClass::OnMyCommand()
    {
        // handle the command
    }

    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)
    {
        // set the UI state with pCmdUI
    }

    BOOL CMyClass::OnComplexCommand(UINT nID)
    {
        // handle the command
        return TRUE;
    }
    ```

Les utilisateurs avancés peuvent gérer une plage de commandes à l’aide d’un gestionnaire de commandes unique : [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) ou ON_COMMAND_RANGE_EX. Pour plus d’informations sur ces macros, consultez la documentation du produit.

> [!NOTE]
> ClassWizard prend en charge la création de gestionnaires d’ON_COMMAND et de ON_UPDATE_COMMAND_UI, mais ne prend pas en charge la création de ON_COMMAND_EX ou de gestionnaires de ON_COMMAND_RANGE. Toutefois, l’Assistant classe effectue une analyse et vous permet de parcourir les quatre variantes du gestionnaire de commandes.

## <a name="control-notification-messages"></a>Contrôler les messages de notification

Les messages envoyés à partir de contrôles enfants dans une fenêtre ont un peu d’informations dans leur entrée de la table des messages : l’ID du contrôle. Le gestionnaire de messages spécifié dans une entrée de la table des messages est appelé uniquement si les conditions suivantes sont vraies :

- Le code de notification de contrôle (mot haut de *lParam*), tel que BN_CLICKED, correspond au code de notification spécifié dans l’entrée de la table des messages.

- L’ID de contrôle (*wParam*) correspond à l’ID de contrôle spécifié dans l’entrée de la table des messages.

Les messages de notification de contrôle personnalisé peuvent utiliser la macro [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) pour définir une entrée de la table des messages avec un code de notification personnalisé. Cette macro se présente sous la forme

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Pour une utilisation avancée [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) peut être utilisé pour gérer une notification de contrôle spécifique à partir d’une plage de contrôles avec le même gestionnaire.

> [!NOTE]
> ClassWizard ne prend pas en charge la création d’un gestionnaire de ON_CONTROL ou de ON_CONTROL_RANGE dans l’interface utilisateur. Vous devez les entrer manuellement avec l’éditeur de texte. ClassWizard analyse ces entrées et vous permet de les parcourir comme n’importe quelle autre entrée de la table des messages.

Les contrôles communs Windows utilisent la [WM_NOTIFY](/windows/win32/controls/wm-notify) plus puissante pour les notifications de contrôle complexes. Cette version de MFC prend en charge directement ce nouveau message à l’aide des macros ON_NOTIFY et ON_NOTIFY_RANGE. Pour plus d’informations sur ces macros, consultez la documentation du produit.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
