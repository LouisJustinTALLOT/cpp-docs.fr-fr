---
title: 'TN006 : Tables des messages | Documents Microsoft'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c4bc820c6b54e055235c1bd29bd55ccfc032c92
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121674"
---
# <a name="tn006-message-maps"></a>TN006 : tables des messages

Cette note décrit la fonctionnalité de mappage de messages MFC.

## <a name="the-problem"></a>Le problème

Microsoft Windows implémente des fonctions virtuelles dans les classes de fenêtre qui utilisent la fonction de messagerie. En raison du grand nombre de messages impliquée, en fournissant une fonction virtuelle distincte pour chaque message Windows créerait un vtable trop importante.

Étant donné que le nombre de messages de Windows définis par le système change au fil du temps, et les tables des messages, car les applications peuvent définir leurs propres messages Windows, fournir un niveau d’indirection qui empêche les modifications de l’interface à partir de la rupture du code existant.

## <a name="overview"></a>Vue d'ensemble

MFC fournit une alternative à l’instruction switch qui a été utilisée dans des programmes Windows traditionnels pour traiter les messages envoyés à une fenêtre. Un mappage à partir des messages aux méthodes peut être défini lorsqu’un message est reçu par une fenêtre, la méthode appropriée est appelée automatiquement. Cette fonctionnalité de la table des messages est conçue pour ressembler à des fonctions virtuelles, mais présente des avantages supplémentaires n’est pas possibles avec les fonctions virtuelles C++.

## <a name="defining-a-message-map"></a>Définition d’une table des messages

Le [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) macro déclare trois membres d’une classe.

- Un tableau privé d’entrées AFX_MSGMAP_ENTRY appelé *_messageEntries*.

- Une structure AFX_MSGMAP protégée appelée *messageMap* qui pointe vers le *_messageEntries* tableau.

- A protégé par la fonction virtuelle appelée `GetMessageMap` qui retourne l’adresse de *messageMap*.

Cette macro doit être placée dans la déclaration d’une classe à l’aide des tables des messages. Par convention, il est à la fin de la déclaration de classe. Exemple :

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

Il s’agit du format généré par AppWizard et ClassWizard lorsqu’ils créent de nouvelles classes. La / / {{et / /}} crochets sont nécessaires pour ClassWizard.

Tableau de la table des messages est définie à l’aide d’un ensemble de macros qui s’étendent aux entrées de mappage de message. Un tableau commence par un [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) appel de macro qui définit la classe qui est gérée par ce mappage de message et la classe parente à laquelle les messages non prise en charge sont passés. Le tableau se termine par le [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) appel de macro.

Entre les appels de ces deux macros est une entrée pour chaque message d’être géré par ce mappage de message. Tous les messages Windows standard a une macro sous la forme ON_WM_*MESSAGE_NAME* qui génère une entrée pour ce message.

Une signature de fonction standard a été définie pour décompresser les paramètres de chaque message Windows et de fournir la sécurité de type. Ces signatures peuvent être trouvées dans le fichier Afxwin.h dans la déclaration de [CWnd](../mfc/reference/cwnd-class.md). Chacun d’eux est marqué avec le mot clé **afx_msg** pour faciliter l’identification.

> [!NOTE]
> ClassWizard exige que vous utilisiez le **afx_msg** mot clé dans les déclarations de gestionnaire de mappage de message.

 Ces signatures de fonction ont été dérivées à l’aide d’une convention simple. Le nom de la fonction commence toujours par `"On`». Il est suivi par le nom du message Windows avec « WM_ » supprimé et la première lettre de chaque mot en majuscules. L’ordre des paramètres est *wParam* suivie `LOWORD`(*lParam*) puis `HIWORD`(*lParam*). Les paramètres inutilisés ne sont pas transmis. Tous les handles qui sont encapsulés par les classes MFC sont convertis en pointeurs vers les objets MFC appropriés. L’exemple suivant montre comment gérer le message WM_PAINT et provoquer la `CMyWnd::OnPaint` fonction à appeler :

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

 Le tableau de mappage de message doit être défini en dehors de toute définition de fonction ou une classe. Il ne doit pas être placé dans un bloc d’extern « C ».

> [!NOTE]
> ClassWizard modifiera les entrées de mappage de message qui se produisent entre le / / {{et / /}} crochet de commentaire.

## <a name="user-defined-windows-messages"></a>Messages Windows défini par l’utilisateur

Les messages définis par l’utilisateur peuvent être inclus dans une table des messages à l’aide de la [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) (macro). Cette macro accepte un numéro de message et une méthode sous la forme :

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

Dans cet exemple, nous établissons un gestionnaire pour un message personnalisé qui a un ID de message Windows dérivé de la base de WM_USER standard pour les messages définis par l’utilisateur. L’exemple suivant montre comment appeler ce gestionnaire :

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

La plage des messages définis par l’utilisateur qui utilisent cette approche doit être comprise entre WM_USER et 0x7fff.

> [!NOTE]
> ClassWizard ne prend pas en charge les routines du gestionnaire ON_MESSAGE saisies à partir de l’interface utilisateur de ClassWizard. Vous devez les entrer manuellement à partir de l’éditeur de Visual C++. ClassWizard analysera ces entrées et vous permettre de les parcourir tout comme les autres entrées de table des messages.

## <a name="registered-windows-messages"></a>Messages Windows inscrits

Le [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) fonction est utilisée pour définir un nouveau message de fenêtre est assuré d’être uniques dans le système. La macro ON_REGISTERED_MESSAGE permet de gérer ces messages. Cette macro accepte un nom d’un *UINT près* variable qui contient l’ID de message windows inscrits. Exemple :

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

La variable ID de message enregistrée Windows (WM_FIND dans cet exemple) doit être un *NEAR* variable en raison du mode ON_REGISTERED_MESSAGE est implémentée.

La plage des messages définis par l’utilisateur qui utilisent cette approche sera dans la plage 0xC000 à 0xFFFF.

> [!NOTE]
> ClassWizard ne prend pas en charge les routines du gestionnaire ON_REGISTERED_MESSAGE saisies à partir de l’interface utilisateur de ClassWizard. Vous devez les entrer manuellement à partir de l’éditeur de texte. ClassWizard analysera ces entrées et vous permettre de les parcourir tout comme les autres entrées de table des messages.

## <a name="command-messages"></a>Messages de commande

Messages de commande à partir des menus et les raccourcis sont gérées dans les tables des messages avec le ON_COMMAND (macro). Cette macro accepte un ID de commande et une méthode. Uniquement le message WM_COMMAND spécifique qui a un *wParam* égale à la commande spécifiée ID est géré par la méthode spécifiée dans l’entrée de table des messages. Fonctions de membre de gestionnaires de commandes n’acceptent aucun paramètre et retourner **void**. La macro a la forme suivante :

```cpp
ON_COMMAND(id, memberFxn)
```

Messages de mise à jour de commande sont routées via le même mécanisme, mais utilisent à la place de la macro ON_UPDATE_COMMAND_UI. Fonctions membres de gestionnaire de mise à jour de commande prennent un seul paramètre, un pointeur vers un [CCmdUI](../mfc/reference/ccmdui-class.md) de l’objet et retourner **void**. La macro a la forme

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Utilisateurs expérimentés peuvent utiliser le ON_COMMAND_EX (macro), qui est une forme étendue de gestionnaires de messages de commande. La macro fournit un sur-ensemble de la fonctionnalité ON_COMMAND. Fonctions membres de gestionnaire de commandes étendue prennent un seul paramètre, un **UINT** qui contient l’ID de commande et retournent un **BOOL**. La valeur de retour doit être **TRUE** pour indiquer que la commande a été gérée. Routage dans le cas contraire, il continuera à d’autres objets cibles de commande.

Exemples de ces formes :

- À l’intérieur Resource.h (généralement généré par Visual C++)

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

- À l’intérieur de la définition de mappage de message

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

 Les utilisateurs expérimentés peuvent gérer un éventail de commandes à l’aide d’un gestionnaire de commandes unique : [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) ou ON_COMMAND_RANGE_EX. Consultez la documentation du produit pour plus d’informations sur ces macros.

> [!NOTE]
> ClassWizard prend en charge la création des gestionnaires ON_COMMAND et ON_UPDATE_COMMAND_UI, mais ne prend pas en charge les gestionnaires ON_COMMAND_EX ou ON_COMMAND_RANGE création. Toutefois, Assistant classe analysera et vous permettent de parcourir toutes les variantes de gestionnaire de quatre commandes.

## <a name="control-notification-messages"></a>Messages de Notification de contrôle

Entrée de plan des messages qui sont envoyés à partir de contrôles enfants dans une fenêtre ont un extra bit d’informations dans le message : ID de. du contrôle Le Gestionnaire de messages spécifié dans une entrée de mappage de message est appelé uniquement si les conditions suivantes sont remplies :

- Le code de notification de contrôle (mot de poids fort *lParam*), tel que BN_CLICKED, correspond au code de notification spécifié dans l’entrée de table des messages.

- L’ID de contrôle (*wParam*) correspond à l’ID du contrôle spécifié dans l’entrée de table des messages.

Les messages de notification de contrôle personnalisé peuvent utiliser le [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) (macro) pour définir une entrée de mappage de message avec un code de notification personnalisée. Cette macro présente sous la forme

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

L’utilisation avancée [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) peut être utilisé pour gérer une notification de contrôle spécifique à partir d’une plage de contrôles avec le même gestionnaire.

> [!NOTE]
> ClassWizard ne prend pas en charge la création d’un gestionnaire ON_CONTROL ou ON_CONTROL_RANGE dans l’interface utilisateur. Vous devez les entrer manuellement avec l’éditeur de texte. ClassWizard analysera ces entrées et vous permettre de les parcourir tout comme les autres entrées de mappage de message.

Les contrôles communs Windows utilisent le plus puissant [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) pour les notifications de contrôle complexe. Cette version de la bibliothèque MFC a une prise en charge directe pour ce nouveau message à l’aide de macros ON_NOTIFY et ON_NOTIFY_RANGE. Consultez la documentation du produit pour plus d’informations sur ces macros.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)  
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)  
