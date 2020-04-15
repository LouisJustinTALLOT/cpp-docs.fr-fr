---
title: 'TN026 : routines DDX et DDV'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 711d433b51ca09836f372d09a11f86c28b82cce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370345"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026 : routines DDX et DDV

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’architecture d’échange de données de dialogue (DDX) et de validation des données de dialogue (DDV). Il décrit également comment vous écrivez une procédure de DDX_ ou de DDV_ et comment vous pouvez étendre ClassWizard à utiliser vos routines.

## <a name="overview-of-dialog-data-exchange"></a>Aperçu de Dialog Data Exchange

Toutes les fonctions de données de dialogue sont effectuées avec le code C. Il n’y a pas de ressources spéciales ou de macros magiques. Le cœur du mécanisme est une fonction virtuelle qui est remplacée dans chaque classe de dialogue qui ne dialoguer l’échange de données et la validation. On le trouve toujours sous cette forme :

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

Le format spécial afX commentaires permettent ClassWizard de localiser et de modifier le code dans cette fonction. Le code qui n’est pas compatible avec ClassWizard doit être placé en dehors des commentaires de format spécial.

Dans l’exemple \<ci-dessus, data_exchange_function_call> est sous la forme:

```cpp
DDX_Custom(pDX, nIDC, field);
```

et \<data_validation_function_call> est facultative et se forme :

```cpp
DDV_Custom(pDX, field, ...);
```

Plus d’une paire DDX_/DDV_ peut être incluse `DoDataExchange` dans chaque fonction.

Voir 'afxdd_.h' pour une liste de toutes les routines d’échange de données de dialogue et les routines de validation des données de dialogue fournies avec MFC.

Les données du dialogue sont juste `CMyDialog` que: les données des membres dans la classe. Il n’est pas stocké dans une struction ou quoi que ce soit de similaire.

## <a name="notes"></a>Notes

Bien que nous appelions ces « données de dialogue `CWnd` », toutes les fonctionnalités sont disponibles dans n’importe quelle classe dérivée et ne se limitent pas aux dialogues.

Les valeurs initiales de données sont définies dans le `//{{AFX_DATA_INIT` constructeur `//}}AFX_DATA_INIT` standard de C, généralement dans un bloc avec et commentaires.

`CWnd::UpdateData`est l’opération qui fait l’initialisation `DoDataExchange`et la manipulation d’erreur autour de l’appel à .

Vous pouvez `CWnd::UpdateData` appeler à tout moment pour effectuer l’échange et la validation des données. Par `UpdateData`défaut (TRUE) est `CDialog::OnOK` appelé `UpdateData`dans le gestionnaire par `CDialog::OnInitDialog`défaut et (FALSE) est appelé dans la par défaut .

La routine DDV_ devrait immédiatement suivre la routine DDX_ pour ce *domaine*.

## <a name="how-does-it-work"></a>Comment fonctionne-t-il

Vous n’avez pas besoin de comprendre ce qui suit afin d’utiliser les données de dialogue. Cependant, comprendre comment cela fonctionne dans les coulisses vous aidera à écrire votre propre procédure d’échange ou de validation.

La `DoDataExchange` fonction de membre `Serialize` est un peu comme la fonction membre - il est responsable d’obtenir ou de définir des données à /à partir d’une forme externe (dans ce cas les contrôles dans un dialogue) à partir/ à des données des membres dans la classe. Le paramètre *pDX* est le contexte pour `CArchive` faire `CObject::Serialize`l’échange de données et est similaire au paramètre à . Le *pDX* `CDataExchange` (un objet) a `CArchive` un drapeau de direction un peu comme a un drapeau de direction:

- Si, `!m_bSaveAndValidate`puis charger l’état des données dans les contrôles.

- Si `m_bSaveAndValidate`, puis définir l’état des données à partir des contrôles.

La validation `m_bSaveAndValidate` ne se produit que lorsque elle est réglée. La valeur `m_bSaveAndValidate` de est déterminée par `CWnd::UpdateData`le paramètre BOOL à .

Il y a `CDataExchange` trois autres membres intéressants :

- `m_pDlgWnd`: La fenêtre (généralement un dialogue) qui contient les commandes. Il s’agit d’empêcher les appelants de la DDX_ et DDV_ fonctions mondiales d’avoir à passer «cela» à chaque routine DDX /DDV.

- `PrepareCtrl`, `PrepareEditCtrl`et : prépare un contrôle de dialogue pour l’échange de données. Stocke la poignée de ce contrôle pour définir la mise au point en cas de panne d’une validation. `PrepareCtrl`est utilisé pour les `PrepareEditCtrl` contrôles non-modification et est utilisé pour les contrôles de modification.

- `Fail`: Appelé après avoir apporté une boîte de message alertant l’utilisateur de l’erreur d’entrée. Cette routine rétablira l’accent sur le `PrepareCtrl` dernier `PrepareEditCtrl`contrôle (le dernier appel ou ) et lancera une exception. Cette fonction de membre peut être appelée à la fois de DDX_ et de routines DDV_.

## <a name="user-extensions"></a>Extensions de l’utilisateur

Il existe plusieurs façons d’étendre le mécanisme par défaut DDX/DDV. Vous pouvez :

- Ajoutez de nouveaux types de données.

    ```cpp
    CTime
    ```

- Ajouter de nouvelles procédures d’échange (DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Ajouter de nouvelles procédures de validation (DDV_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Transmettre des expressions arbitraires aux procédures de validation.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Ces expressions arbitraires ne peuvent pas être modifiées par ClassWizard et doivent donc être déplacées en dehors des commentaires de format spécial (/AFX_DATA_MAP (CMyClass)).

La `DoDialogExchange` fonction de membre inclut des conditions ou tout autre relevé de Cmd valide avec des appels de fonction d’échange et de validation entremêlés.

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> Comme indiqué ci-dessus, ce code ne peut pas être modifié par ClassWizard et ne doit être utilisé qu’en dehors des commentaires format spécial.

## <a name="classwizard-support"></a>Soutien ClassWizard

ClassWizard prend en charge un sous-ensemble de personnalisations DDX/DDV en vous permettant d’intégrer vos propres routines DDX_ et DDV_ dans l’interface utilisateur ClassWizard. Cela n’est avantageux que si vous prévoyez de réutiliser des routines particulières DDX et DDV dans un projet ou dans de nombreux projets.

Pour ce faire, des entrées spéciales sont faites dans DDX. CLW (versions précédentes de Visual CMD a stocké ces informations dans APSTUDIO. INI) ou dans votre projet . Fichier CLW. Les entrées spéciales peuvent être inscrites soit dans la section [Informations générales] de votre projet . fichier CLW ou dans la section [ExtraDDX] du DDX. Fichier CLW dans le répertoire 'Program Files’Microsoft Visual Studio’Visual C’bin. Vous devrez peut-être créer le DDX. Fichier CLW s’il n’existe pas déjà. Si vous prévoyez d’utiliser les routines personnalisées DDX_/DDV_ uniquement dans un certain projet, ajoutez les entrées à la section [Informations générales] de votre projet . Fichier CLW à la place. Si vous prévoyez d’utiliser les routines sur de nombreux projets, ajoutez les entrées à la section [ExtraDDX] de DDX. CLW.

Le format général de ces entrées spéciales est :

> ExtraDDXCount*n*

où *n* est le nombre d’ExtraDDX? lignes à suivre, de la forme

> Clés ExtraDDX?MD*keys*; *vb-clés*; *prompte*; *type*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

Où? est un numéro 1 - *n* indiquant quel type DDX dans la liste qui est définie.

Chaque champ est délimité par un caractère ';'. Les champs et leur but sont décrits ci-dessous.

- *Clés*

  Une liste de caractères uniques indiquant pour quel dialogue contrôle ce type variable est autorisée.

  |Caractère|Contrôle autorisé|
  |-|-|
  E | modifier
  C | boîte à cocher à deux états
  c | boîte à cocher à trois états
  R | premier bouton radio dans un groupe
  L | boîte de liste non-triée
  l | boîte de liste triée
  M | boîte combo (avec article d’édition)
  N | liste de drop nonsorted
  n | liste de drop trié
  1 | si l’insert DDX doit être ajouté à la tête de liste (par défaut est ajouté à la queue) Ceci est généralement utilisé pour les routines DDX qui transfèrent la propriété «Contrôle».

- *vb-clés*

  Ce champ n’est utilisé que dans le produit 16 bits pour les commandes VBX (les commandes VBX ne sont pas prises en charge dans le produit 32 bits)

- *Invite*

  Chaîne à placer dans la boîte combo Propriété (pas de citations)

- *type*

  Identifiant unique pour le type à émettre dans le fichier d’en-tête. Dans notre exemple ci-dessus avec DDX_Time, cela serait réglé sur CTime.

- *vb-clés*

  Pas utilisé dans cette version et doit toujours être vide

- *initValue*

  Valeur initiale — 0 ou blanc. S’il est vierge, aucune ligne d’initialisation ne sera écrite dans la section de l’AFX_DATA_INIT application de la page de mise en œuvre. Une entrée vierge doit être utilisée pour `CString`les `CTime`objets CMD (tels que, , et ainsi de suite) qui ont des constructeurs qui garantissent une initialisation correcte.

- *DDX_Proc*

  Identifiant unique pour la procédure DDX_. Le nom de la fonction CMD doit commencer par « DDX_ », mais n’incluez pas « DDX_ » dans l’identificateur \<> DDX_Proc. Dans l’exemple \<ci-dessus, le DDX_Proc>'identifiant serait le temps. Lorsque ClassWizard écrit l’appel de fonction au fichier d’implémentation dans la section AFX_DATA_MAP, il joint ce nom à DDX_, arrivant ainsi à DDX_Time.

- *Commentaire*

  Commentaire à afficher dans le dialogue pour variable avec ce DDX. Placez n’importe quel texte que vous souhaitez ici, et fournissez habituellement quelque chose qui décrit l’opération effectuée par la paire DDX/DDV.

- *DDV_Proc*

  La partie DDV de l’entrée est facultative. Toutes les routines DDX n’ont pas de routines DDV correspondantes. Souvent, il est plus pratique d’inclure la phase de validation comme partie intégrante du transfert. C’est souvent le cas lorsque votre routine DDV ne nécessite aucun paramètre, car ClassWizard ne prend pas en charge les routines DDV sans aucun paramètre.

- *Arg*

  Identifiant unique pour la procédure DDV_. Le nom de la fonction CMD doit commencer par « DDV_ », mais \<n’inclut pas « DDX_ » dans l’identificateur> DDX_Proc.

  *arg* est suivi par 1 ou 2 args DDV:

  - *promptN*

      Chaîne à placer au-dessus de l’élément d’édition (avec & pour l’accélérateur).

  - *fmtN fmtN*

      Caractère format pour le type arg, l’un des:

      |Caractère|Type|
      |-|-|
      |d | int|
      |u | nombre entier non signé|
      |D | longue int (c’est-à-dire, long)|
      |U | longtemps non signé (c’est-à-dire DWORD)|
      |f | float|
      |F | double|
      |s | string|

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
