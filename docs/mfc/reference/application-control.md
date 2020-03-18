---
title: Contrôle d'application
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418901"
---
# <a name="application-control"></a>Contrôle d'application

OLE nécessite un contrôle substantiel sur les applications et leurs objets. Les DLL système OLE doivent être en mesure de lancer et de libérer des applications automatiquement, de coordonner leur production et leur modification d’objets, et ainsi de suite. Les fonctions de cette rubrique répondent à ces exigences. En plus d’être appelé par les DLL système OLE, ces fonctions doivent également être appelées par des applications.

### <a name="application-control"></a>Contrôle d'application

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Indique si l’application peut se terminer.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Récupère le filtre de messages actuel de l’application.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Récupère l’indicateur de contrôle utilisateur actuel.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Définit ou efface l’indicateur de contrôle utilisateur.|
|[AfxOleLockApp](#afxolelockapp)|Incrémente le décompte global de l’infrastructure du nombre d’objets actifs dans une application.|
|[AfxOleLockControl](#afxolelockcontrol)| Verrouille la fabrique de classe du contrôle spécifié. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Décrémente le nombre de frameworks du nombre d’objets actifs dans une application.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Déverrouille la fabrique de classe du contrôle spécifié. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Inscrit un serveur dans le registre système OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implémente l’interface utilisateur pour la commande d’objet *TypeName* .|

##  <a name="afxolecanexitapp"></a>AfxOleCanExitApp

Indique si l’application peut se terminer.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’application peut se fermer ; Sinon, 0.

### <a name="remarks"></a>Notes

Une application ne doit pas se terminer s’il existe des références en suspens à ses objets. Les fonctions globales `AfxOleLockApp` et `AfxOleUnlockApp` incrémentation et décrémentation, respectivement, un compteur de références aux objets de l’application. L’application ne doit pas se terminer lorsque ce compteur est différent de zéro. Si le compteur est différent de zéro, la fenêtre principale de l’application est masquée (non détruite) lorsque l’utilisateur choisit fermer dans le menu système ou quitter dans le menu fichier. L’infrastructure appelle cette fonction dans `CFrameWnd::OnClose`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

##  <a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Récupère le filtre de messages actuel de l’application.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le filtre de messages actuel.

### <a name="remarks"></a>Notes

Appelez cette fonction pour accéder à l’objet actuel dérivé de `COleMessageFilter`, de la même façon que vous appelez `AfxGetApp` pour accéder à l’objet d’application actuel.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête**: AFXWIN. h

##  <a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Récupère l’indicateur de contrôle utilisateur actuel.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur est dans le contrôle de l’application ; Sinon, 0.

### <a name="remarks"></a>Notes

L’utilisateur contrôle l’application lorsque l’utilisateur a explicitement ouvert ou créé un nouveau document. L’utilisateur contrôle également si l’application n’a pas été lancée par les dll du système OLE, en d’autres termes, si l’utilisateur a lancé l’application avec l’interpréteur de commandes système.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

##  <a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Définit ou efface l’indicateur de contrôle utilisateur, qui est expliqué dans la référence pour `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Paramètres

*bUserCtrl*<br/>
Spécifie si l’indicateur de contrôle utilisateur doit être défini ou effacé.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction lorsque l’utilisateur crée ou charge un document, mais pas lorsqu’un document est chargé ou créé via une action indirecte telle que le chargement d’un objet incorporé à partir d’une application conteneur.

Appelez cette fonction si d’autres actions dans votre application doivent mettre l’utilisateur au contrôle de l’application.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

##  <a name="afxolelockapp"></a>AfxOleLockApp

Incrémente le décompte global de l’infrastructure du nombre d’objets actifs dans l’application.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Notes

L’infrastructure conserve le nombre d’objets actifs dans une application. Les fonctions `AfxOleLockApp` et `AfxOleUnlockApp`, respectivement, incrémentent et décrémentent ce nombre.

Lorsque l’utilisateur tente de fermer une application qui a des objets actifs (une application pour laquelle le nombre d’objets actifs est différent de zéro), l’infrastructure masque l’application à partir de la vue de l’utilisateur au lieu de l’arrêter complètement. La fonction `AfxOleCanExitApp` indique si l’application peut se terminer.

Appelez `AfxOleLockApp` à partir de n’importe quel objet qui expose des interfaces OLE, si ce n’est pas souhaitable pour que cet objet soit détruit tout en étant toujours utilisé par une application cliente. Appelez également `AfxOleUnlockApp` dans le destructeur de tout objet qui appelle `AfxOleLockApp` dans le constructeur. Par défaut, les `COleDocument` (et les classes dérivées) verrouillent et déverrouillent automatiquement l’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

##  <a name="afxoleunlockapp"></a>AfxOleUnlockApp

Décrémente le nombre d’objets actifs de l’infrastructure dans l’application.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez `AfxOleLockApp`.

Lorsque le nombre d’objets actifs atteint zéro, `AfxOleOnReleaseAllObjects` est appelée.

### <a name="example"></a>Exemple

Consultez l’exemple pour [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Verrouille la fabrique de classe du contrôle spécifié afin que les données créées dynamiquement associées au contrôle restent en mémoire.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
ID de classe unique du contrôle.

*lpszProgID*<br/>
ID de programme unique du contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fabrique de classe du contrôle a été verrouillée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Cela peut considérablement accélérer l’affichage des contrôles. Par exemple, une fois que vous avez créé un contrôle dans une boîte de dialogue et verrouillé le contrôle avec `AfxOleLockControl`, vous n’avez pas besoin de le créer et de le supprimer à chaque fois que la boîte de dialogue est affichée ou détruite. Si l’utilisateur ouvre et ferme une boîte de dialogue à plusieurs reprises, le verrouillage de vos contrôles peut considérablement améliorer les performances. Lorsque vous êtes prêt à détruire le contrôle, appelez `AfxOleUnlockControl`.

### <a name="example"></a>Exemple

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

Cette fonction vous permet d’inscrire votre serveur dans le registre système OLE.

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
Référence à l’ID de classe OLE du serveur.

*lpszClassName*<br/>
Pointeur vers une chaîne contenant le nom de la classe des objets du serveur.

*lpszShortTypeName*<br/>
Pointeur vers une chaîne contenant le nom abrégé du type d’objet du serveur, tel que « Chart ».

*lpszLongTypeName*<br/>
Pointeur vers une chaîne contenant le nom long du type d’objet du serveur, par exemple « Microsoft Excel 5,0 Chart ».

*nAppType*<br/>
Valeur, extraite de l’énumération OLE_APPTYPE, spécifiant le type d’application OLE. Les valeurs possibles sont les suivantes :

- OAT_INPLACE_SERVER serveur dispose de l’interface utilisateur complète du serveur.

- OAT_SERVER Server prend uniquement en charge l’incorporation.

- OAT_CONTAINER conteneur prend en charge les liens vers les incorporations.

- OAT_DISPATCH_OBJECT objet `IDispatch`.

*rglpszRegister*<br/>
Tableau de pointeurs vers des chaînes représentant les clés et valeurs à ajouter au registre système OLE si aucune valeur existante n’est trouvée pour les clés.

*rglpszOverwrite*<br/>
Tableau de pointeurs vers des chaînes représentant les clés et valeurs à ajouter au registre système OLE si le registre contient des valeurs existantes pour les clés données.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la classe de serveur est inscrite avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

La plupart des applications peuvent utiliser `COleTemplateServer::Register` pour inscrire les types de document de l’application. Si le format de Registre système de votre application ne correspond pas au modèle classique, vous pouvez utiliser `AfxOleRegisterServerClass` pour davantage de contrôle.

Le Registre se compose d’un ensemble de clés et de valeurs. Les arguments *rglpszRegister* et *rglpszOverwrite* sont des tableaux de pointeurs vers des chaînes, chacun composé d’une clé et d’une valeur séparés par un caractère **null** (`'\0'`). Chacune de ces chaînes peut avoir des paramètres remplaçables dont les emplacements sont marqués par les séquences de caractères *%1* à *%5*.

Les symboles sont remplis comme suit :

|Symbole|Valeur|
|------------|-----------|
|%1|ID de classe, mis en forme en tant que chaîne|
|%2|Nom de la classe|
|%3|Chemin d’accès au fichier exécutable|
|4|Nom de type abrégé|
|%5|Nom de type long|

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

##  <a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implémente l’interface utilisateur pour la commande d’objet *TypeName* .

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>Paramètres

*pClient*<br/>
Pointeur vers l’élément OLE du client.

*pMenu*<br/>
Pointeur vers l’objet de menu à mettre à jour.

*iMenuItem*<br/>
Index de l’élément de menu à mettre à jour.

*nIDVerbMin*<br/>
ID de commande qui correspond au verbe principal.

*nIDVerbMax*<br/>
ID de commande qui correspond au dernier verbe.

*nIDConvert*<br/>
ID de l’élément de menu Convert.

### <a name="remarks"></a>Notes

Si le serveur reconnaît uniquement un verbe principal, l’élément de menu devient « objet de verbe *TypeName* » et la commande *nIDVerbMin* est envoyée lorsque l’utilisateur choisit la commande. Si le serveur reconnaît plusieurs verbes, l’élément de menu devient « Object *TypeName* » et un sous-menu qui répertorie tous les verbes s’affiche lorsque l’utilisateur choisit la commande. Lorsque l’utilisateur choisit un verbe dans le sous-menu, *nIDVerbMin* est envoyé si le premier verbe est choisi, *nIDVerbMin* + 1 est envoyé si le deuxième verbe est choisi, et ainsi de suite. L’implémentation par défaut de `COleDocument` gère automatiquement cette fonctionnalité.

Vous devez disposer de l’instruction suivante dans le script de ressources de l’application de votre client (. RC) :

**#include \<AFXOLECL. RC >**

### <a name="requirements"></a>Spécifications

**En-tête**: AFXOLE. h

## <a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

Déverrouille la fabrique de classe du contrôle spécifié.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
ID de classe unique du contrôle.

*lpszProgID*<br/>
ID de programme unique du contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fabrique de classe du contrôle a été déverrouillée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Un contrôle est verrouillé avec `AfxOleLockControl`, afin que les données créées dynamiquement associées au contrôle restent en mémoire. Cela peut considérablement accélérer l’affichage du contrôle, car le contrôle n’a pas besoin d’être créé et détruit à chaque fois qu’il est affiché. Lorsque vous êtes prêt à détruire le contrôle, appelez `AfxOleUnlockControl`.

### <a name="example"></a>Exemple

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="see-also"></a>Voir aussi

[Macros et globales](mfc-macros-and-globals.md)<br/>
