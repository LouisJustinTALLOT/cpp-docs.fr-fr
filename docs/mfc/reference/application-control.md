---
title: Contrôle d'application
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 1f438d3344e90a16def2bd4c0f9cedcd47a64203
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363554"
---
# <a name="application-control"></a>Contrôle d'application

OLE nécessite un contrôle substantiel sur les applications et leurs objets. Les DLL système OLE doivent être en mesure de lancer et de libérer des applications automatiquement, de coordonner leur production et leur modification d’objets, et ainsi de suite. Les fonctions dans ce domaine répondent à ces exigences. En plus d’être appelé par le système OLE DLLs, ces fonctions doivent parfois être appelées par les applications ainsi.

### <a name="application-control"></a>Contrôle d'application

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Indique si la demande peut se terminer.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Récupère le filtre de message actuel de l’application.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Récupère le drapeau de contrôle de l’utilisateur actuel.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Définit ou efface le drapeau de contrôle de l’utilisateur.|
|[AfxOleLockApp](#afxolelockapp)|Incréments le nombre global d’objets actifs dans une application.|
|[AfxOleLockControl](#afxolelockcontrol)| Verrouille l’usine de classe du contrôle spécifié. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Écarte le nombre d’objets actifs dans une application.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Débloque l’usine de classe du contrôle spécifié. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Enregistre un serveur dans le registre du système OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implémente l’interface utilisateur pour la commande *d’objet de type.*|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a>AfxOleCanExitApp

Indique si la demande peut se terminer.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’application peut sortir; sinon 0.

### <a name="remarks"></a>Notes

Une application ne doit pas se terminer s’il y a des références exceptionnelles à ses objets. Les fonctions `AfxOleLockApp` `AfxOleUnlockApp` globales et l’incrément et la décroission, respectivement, un compteur de références aux objets de l’application. L’application ne doit pas se terminer lorsque ce compteur n’est pas zéro. Si le compteur n’est pas zéro, la fenêtre principale de l’application est cachée (non détruite) lorsque l’utilisateur choisit Close à partir du menu du système ou de sortie du menu Fichier. Le cadre appelle `CFrameWnd::OnClose`cette fonction dans .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter AfxOleGetMessageFilter

Récupère le filtre de message actuel de l’application.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le filtre de message actuel.

### <a name="remarks"></a>Notes

Appelez cette fonction pour `COleMessageFilter`accéder à l’objet `AfxGetApp` dérivé actuel, tout comme vous appelleriez pour accéder à l’objet d’application actuel.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête**: afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Récupère le drapeau de contrôle de l’utilisateur actuel.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur est en contrôle de l’application; sinon 0.

### <a name="remarks"></a>Notes

L’utilisateur contrôle l’application lorsque l’utilisateur a explicitement ouvert ou créé un nouveau document. L’utilisateur est également en contrôle si l’application n’a pas été lancée par le système OLE DLLs - en d’autres termes, si l’utilisateur a lancé l’application avec la coque du système.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Définit ou efface le drapeau de contrôle de l’utilisateur, qui est expliqué dans la référence pour `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Paramètres

*bUserCtrl*<br/>
Précise si le drapeau de contrôle de l’utilisateur doit être défini ou effacé.

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction lorsque l’utilisateur crée ou charge un document, mais pas lorsqu’un document est chargé ou créé par une action indirecte telle que le chargement d’un objet intégré à partir d’une application de conteneur.

Appelez cette fonction si d’autres actions de votre application doivent mettre l’utilisateur en contrôle de l’application.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a>AfxOleLockApp

Incréments le nombre global d’objets actifs dans l’application.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Notes

Le cadre tient compte du nombre d’objets actifs dans une application. Le `AfxOleLockApp` `AfxOleUnlockApp` et les fonctions, respectivement, l’augmentation et la décroissation de ce compte.

Lorsque l’utilisateur tente de fermer une application qui dispose d’objets actifs — une application pour laquelle le nombre d’objets actifs n’est pas zéro — le cadre cache l’application de la vue de l’utilisateur au lieu de l’arrêter complètement. La `AfxOleCanExitApp` fonction indique si l’application peut se terminer.

Appelez `AfxOleLockApp` à partir de tout objet qui expose les interfaces OLE, s’il ne serait pas souhaitable que cet objet soit détruit tout en étant utilisé par une application client. Faites `AfxOleUnlockApp` également appel au destructeur de `AfxOleLockApp` tout objet qui appelle dans le constructeur. Par défaut, `COleDocument` (et les classes dérivées) verrouillent et déverrouillent automatiquement l’application.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a>AfxOleUnlockApp

Décrément le nombre d’objets actifs dans l’application.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Notes

Voir `AfxOleLockApp` pour plus d’informations.

Lorsque le nombre d’objets `AfxOleOnReleaseAllObjects` actifs atteint zéro, est appelé.

### <a name="example"></a>Exemple

Voir l’exemple pour [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Verrouille l’usine de classe du contrôle spécifié de sorte que les données dynamiquement créées associées au contrôle restent dans la mémoire.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
L’ID de classe unique du contrôle.

*lpszProgID*<br/>
L’ID unique du programme du contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’usine de classe du contrôle a été verrouillé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cela peut considérablement accélérer l’affichage des commandes. Par exemple, une fois que vous créez un contrôle `AfxOleLockControl`dans une boîte de dialogue et verrouillez le contrôle avec, vous n’avez pas besoin de le créer et de le tuer à nouveau chaque fois que le dialogue est montré ou détruit. Si l’utilisateur ouvre et ferme une boîte de dialogue à plusieurs reprises, le verrouillage de vos commandes peut améliorer considérablement les performances. Lorsque vous êtes prêt à `AfxOleUnlockControl`détruire le contrôle, appelez .

### <a name="example"></a>Exemple

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

Cette fonction vous permet d’enregistrer votre serveur dans le registre du système OLE.

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

*clsid*<br/>
Référence à l’ID de classe OLE du serveur.

*lpszClassName (en)*<br/>
Pointeur vers une chaîne contenant le nom de classe des objets du serveur.

*lpszShortTypeName*<br/>
Pointeur vers une chaîne contenant le nom court du type d’objet du serveur, tel que "Chart".

*lpszLongTypeName*<br/>
Pointeur vers une chaîne contenant le nom long du type d’objet du serveur, comme "Microsoft Excel 5.0 Chart."

*nAppType (en)*<br/>
Une valeur, tirée du recensement OLE_APPTYPE, spécifiant le type d’application OLE. Les valeurs possibles sont les suivantes :

- OAT_INPLACE_SERVER Server dispose d’une interface utilisateur-utilisateur complète.

- OAT_SERVER Server ne prend en charge que l’intégration.

- OAT_CONTAINER Container prend en charge les liens vers les intégrations.

- `IDispatch`OAT_DISPATCH_OBJECT objet capable.

*rglpszRegister (rglpszRegister)*<br/>
Array de pointeurs aux chaînes représentant les clés et les valeurs à ajouter au registre du système OLE si aucune valeur existante pour les clés n’est trouvée.

*rglpszOverwrite*<br/>
Array de pointeurs aux chaînes représentant les clés et les valeurs à ajouter au registre du système OLE si le registre contient les valeurs existantes pour les clés données.

### <a name="return-value"></a>Valeur de retour

Nonzero si la classe de serveur est enregistrée avec succès; sinon 0.

### <a name="remarks"></a>Notes

La plupart `COleTemplateServer::Register` des applications peuvent être utilisées pour enregistrer les types de documents de l’application. Si le format système-registre de votre application ne correspond `AfxOleRegisterServerClass` pas au modèle typique, vous pouvez utiliser pour plus de contrôle.

Le registre se compose d’un ensemble de clés et de valeurs. Les arguments *rglpszRegister* et *rglpszOverwrite* sont des tableaux de pointeurs aux cordes, **NULL** chacun composé `'\0'`d’une clé et d’une valeur séparée par un personnage NULL ( ). Chacune de ces cordes peut avoir des paramètres remplaçables dont les places sont marquées par les séquences de caractères *%1* à *%5*.

Les symboles sont remplis comme suit :

|Symbole|Value|
|------------|-----------|
|%1|Id de classe, formaté comme une chaîne|
|%2|Nom de classe|
|%3|Chemin vers le fichier exécutable|
|4|Nom de type court|
|%5|Nom de type long|

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu AfxOleSetEditMenu

Implémente l’interface utilisateur pour la commande *d’objet de type.*

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

*pClient (en)*<br/>
Un pointeur à l’élément OLE client.

*pMenu*<br/>
Un pointeur de l’objet du menu à mettre à jour.

*iMenuItem (en anglais)*<br/>
L’index de l’élément de menu à mettre à jour.

*nIDVerbMin (en)*<br/>
L’ID de commande qui correspond au verbe principal.

*nIDVerbMax (en)*<br/>
L’ID de commande qui correspond au dernier verbe.

*nIDConvert*<br/>
ID pour l’élément de menu Convertir.

### <a name="remarks"></a>Notes

Si le serveur ne reconnaît qu’un verbe principal, l’élément du menu devient « objet *de type verbe* » et la commande *nIDVerbMin* est envoyée lorsque l’utilisateur choisit la commande. Si le serveur reconnaît plusieurs verbes, alors l’élément de menu devient « objet *de type* » et un sous-mois énumérant tous les verbes apparaît lorsque l’utilisateur choisit la commande. Lorsque l’utilisateur choisit un verbe du sous-mois, *nIDVerbMin* est envoyé si le premier verbe est choisi, *nIDVerbMin* 1 est envoyé si le deuxième verbe est choisi, et ainsi de suite. L’implémentation par défaut `COleDocument` gère automatiquement cette fonctionnalité.

Vous devez avoir la déclaration suivante dans le script de ressource d’application de votre client (. RC) fichier:

**#include \<>afxolecl.rc**

### <a name="requirements"></a>Spécifications

**En-tête**: afxole.h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

Débloque l’usine de classe du contrôle spécifié.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
L’ID de classe unique du contrôle.

*lpszProgID*<br/>
L’ID unique du programme du contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’usine de classe du contrôle a été débloqué avec succès; sinon 0.

### <a name="remarks"></a>Notes

Un contrôle est `AfxOleLockControl`verrouillé avec , de sorte que les données dynamiquement créées associées au contrôle reste dans la mémoire. Cela peut considérablement accélérer l’affichage du contrôle parce que le contrôle n’a pas besoin d’être créé et détruit chaque fois qu’il est affiché. Lorsque vous êtes prêt à `AfxOleUnlockControl`détruire le contrôle, appelez .

### <a name="example"></a>Exemple

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
