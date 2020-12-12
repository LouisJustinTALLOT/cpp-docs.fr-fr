---
description: 'En savoir plus sur : Guide de Portage : COM Spy'
title: 'Guide du portage : COMSpy'
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: 69a97a04d255e64fdde0d863e637d72dfb238967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322632"
---
# <a name="porting-guide-com-spy"></a>Guide du portage : COMSpy

Cette rubrique est la deuxième d’une série d’articles qui décrit le processus de mise à niveau d’anciens projets Visual Studio C++ vers la dernière version de Visual Studio. L'exemple de code utilisé dans cette rubrique a été compilé avec Visual Studio 2005.

## <a name="comspy"></a>COMSpy

COMSpy est un programme qui surveille et enregistre l'activité des composants de service sur un ordinateur. Les composants de service sont des composants COM+ qui s'exécutent sur un système et peuvent être utilisés par des ordinateurs du même réseau. Ils sont gérés par la fonctionnalité Services de composants disponible dans le Panneau de configuration Windows.

### <a name="step-1-converting-the-project-file"></a>Étape 1. Conversion du fichier projet

Le fichier projet a été rapidement converti, et le processus a généré un rapport de migration. Certaines entrées du rapport signalent d'éventuels problèmes à résoudre. Voici un problème qui a été signalé (notez que, dans cette rubrique, nous avons parfois abrégé les messages d’erreur pour une meilleure lisibilité, par exemple, en supprimant les chemins d’accès complets) :

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

L’un des problèmes fréquents de mise à niveau des projets est que le paramètre OutputFile de l' **éditeur de liens** dans la boîte de dialogue Propriétés du projet doit être examiné. Pour les projets créés dans une version antérieure à Visual Studio 2010, le paramètre OutputFile, quand il n'a pas une valeur standard, n'est pas toujours reconnu par l'Assistant Conversion automatique. Dans ce cas, les chemins des fichiers de sortie ont été définis en fonction d’un dossier non standard, XP32_DEBUG. Pour en savoir plus sur cette erreur, nous avons consulté un [billet de blog](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) traitant de la mise à niveau des projets Visual Studio 2010. Cette mise à niveau a introduit un changement majeur, à savoir le remplacement de vcbuild par msbuild. D’après ces informations, la valeur par défaut du paramètre **Fichier de sortie** au moment de la création d’un projet est `$(OutDir)$(TargetName)$(TargetExt)`. Toutefois, cette valeur n’est pas définie durant la conversion, car les projets convertis ne peuvent pas vérifier que tout est correct. Essayons toutefois d'utiliser cette valeur pour le paramètre OutputFile et voyons si elle est acceptée.  Cela ne pose pas de problème. Nous pouvons donc continuer. S'il n'y a pas de raison particulière justifiant l'utilisation d'un dossier de sortie non standard, nous vous recommandons d'utiliser l'emplacement standard. Dans le cas présent, nous avons choisi de conserver l’emplacement de sortie non standard durant le processus de portage et de mise à niveau. `$(OutDir)` est résolu en dossier XP32_DEBUG dans la configuration **Debug** et en dossier ReleaseU dans la configuration **Release**.

### <a name="step-2-getting-it-to-build"></a>Étape 2. Préparation de la build

Le processus de build du projet porté a généré un certain nombre d'erreurs et d'avertissements.

`ComSpyCtl` ne peut pas être compilé en raison de cette erreur du compilateur :

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

L’erreur référence la méthode `Save` de la classe `IPersistStreamInitImpl` dans atlcom.h.

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

Le problème est qu'une conversion qui était acceptée par une ancienne version du compilateur n'est plus valide. Pour être conforme à la norme C++, du code qui était auparavant accepté ne l'est plus. Dans ce cas, passer un pointeur non const à une fonction qui attend un pointeur const n'est pas une méthode sûre.  La solution consiste à trouver la déclaration de `IPersistStreamInit_Save` sur la classe `CComSpy`, et à ajouter le modificateur const au troisième paramètre.

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

Changez également `IPersistStreamInit_Load` de façon similaire.

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

L'erreur suivante concerne l'inscription.

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

Nous n'avons plus besoin de cette commande d'inscription post-build. Au lieu de cela, nous supprimons simplement la commande de build personnalisée et spécifions dans les paramètres de l' **éditeur de liens** pour inscrire la sortie.

### <a name="dealing-with-warnings"></a>Traitement des avertissements

Le projet génère l'avertissement d'éditeur de liens suivant.

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

L’option de compilateur `/SAFESEH` n’est pas utile en mode debug, contrairement à `/EDITANDCONTINUE`. La solution consiste donc à désactiver `/SAFESEH` pour les configurations **Debug** uniquement. Pour cela, nous ouvrons la boîte de dialogue Propriétés du projet qui génère cette erreur. Nous affectons d’abord à **Configuration** la valeur **Debug** (en fait, **Debug Unicode**), puis dans la section **Avancé** de l’éditeur de liens, nous réaffectons à la propriété **Image avec gestionnaires d’exceptions sécurisés** la valeur **Non** (`/SAFESEH:NO`).

Le compilateur nous avertit que `PROP_ENTRY_EX` est déprécié. Il n’est pas sécurisé, et le remplacement recommandé est `PROP_ENTRY_TYPE_EX`.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Nous modifions le code dans ccomspy.h en conséquence, en ajoutant les types COM appropriés.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Nous arrivons aux derniers avertissements à traiter, qui sont également dus aux vérifications de conformité plus strictes du compilateur :

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

L'avertissement C4018 provient de ce code :

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

Le problème est que `i` est déclaré comme `UINT` et `lCount` est déclaré comme **`long`** , par conséquent l’incompatibilité signed/unsigned. Il serait peu pratique de changer le type de `lCount` en `UINT` , car il obtient sa valeur de `IMtsEventInfo::get_Count` , qui utilise le type **`long`** et n’est pas dans le code utilisateur. Nous préférons ajouter un cast dans le code. Un cast de style C ferait pour un cast numérique comme celui-ci, mais il **`static_cast`** s’agit du style recommandé.

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

Ces avertissements ont été générés parce qu'une variable a été déclarée dans une fonction contenant un paramètre avec le même nom, ce qui peut potentiellement induire une confusion dans le code. Nous avons résolu ce problème en modifiant les noms des variables locales.

### <a name="step-3-testing-and-debugging"></a>Étape 3. Test et débogage

Nous avons testé l'application d'abord en exécutant les différents menus et commandes, puis en fermant l'application. Le seul problème signalé était une assertion de débogage à la fermeture de l'application. Le problème est apparu dans le destructeur de `CWindowImpl`, une classe de base de l’objet `CSpyCon`, composant COM principal de l’application. L'échec d'assertion s'est produit dans le code suivant dans atlwin.h.

```cpp
virtual ~CWindowImplRoot()
{
     #ifdef _DEBUG
     if(m_hWnd != NULL)// should be cleared in WindowProc
     {
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));
          ATLASSERT(FALSE);
     }
     #endif //_DEBUG
}
```

`hWnd` a normalement la valeur zéro dans la fonction `WindowProc`, mais cela n’est pas le cas. Au lieu du `WindowProc` par défaut, un gestionnaire personnalisé est appelé pour le message Windows (WM_SYSCOMMAND) qui ferme la fenêtre. Dans le gestionnaire personnalisé, `hWnd` n’a pas la valeur zéro. En examinant du code similaire dans la classe `CWnd` de MFC, nous voyons que la destruction d’une fenêtre entraîne un appel à `OnNcDestroy`. Dans MFC, la documentation recommande d’appeler le `NcDestroy` de base au moment de la substitution de `CWnd::OnNcDestroy`. Vous avez ainsi la garantie que les opérations de nettoyage nécessaires sont effectuées, notamment la séparation du handle de fenêtre de la fenêtre ou, en d’autres termes, l’affectation à `hWnd` de la valeur zéro. Cette assertion aurait pu aussi être déclenchée dans la version initiale de l'exemple, car le même code d'assertion était présent dans l'ancienne version de atlwin.h.

Pour tester la fonctionnalité de l’application, nous avons créé un **composant desservi** à l’aide du modèle de projet ATL, vous avez choisi d’ajouter la prise en charge de com+ dans l’Assistant Projet ATL. Si vous n’avez pas encore travaillé avec les composants traités, il n’est pas difficile d’en créer un et de les enregistrer et de les rendre disponibles sur le système ou le réseau pour que d’autres applications les utilisent. L'application COMSpy est conçue pour surveiller l'activité des composants de service et servir ainsi d'aide au diagnostic.

Nous avons ensuite ajouté une classe, choisi un objet ATL et spécifié le nom d’objet `Dog`. Puis, dans dog.h et dog.cpp, nous avons ajouté l'implémentation.

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

Ensuite, nous l’avons généré et inscrit (vous devez exécuter Visual Studio en tant qu’administrateur) et vous l’avez activé à l’aide de l’application de **composant de service** dans le panneau de configuration Windows. Nous avons créé un projet Windows Forms C#, fait glisser un bouton sur le formulaire à partir de la boîte à outils et double-cliqué sur un gestionnaire d'événements Click. Nous avons ajouté le code suivant pour instancier le composant `Dog`.

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

Cela a fonctionné sans problème. Avec COMSpy, opérationnel et configuré pour surveiller le composant `Dog`, un grand nombre d’informations relatives à l’activité s’affichent.

## <a name="see-also"></a>Voir aussi

[Portage et mise à niveau : exemples et études de cas](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Exemple suivant : Spy++](../porting/porting-guide-spy-increment.md)<br/>
[Exemple précédent : Scribble MFC](../porting/porting-guide-mfc-scribble.md)
