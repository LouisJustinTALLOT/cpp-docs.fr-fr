---
title: "TN064 : Modèle de thread Apartment dans les contrôles ActiveX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 07730d6c078dcc8fcd7ea1406f8cff6f665c9919
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064 : modèle de thread apartment dans les contrôles ActiveX
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note technique explique comment activer le modèle de thread apartment dans un contrôle ActiveX. Notez que le modèle de thread apartment est pris en charge uniquement dans les versions 4.2 ou ultérieures de Visual C++.  
  
## <a name="what-is-apartment-model-threading"></a>Quel est le modèle de thread Apartment  
 Le modèle apartment est une approche de prise en charge d'objets incorporés, tels que les contrôles ActiveX, dans une application conteneur multithread. Bien que l'application puisse avoir plusieurs threads, chaque instance d'un objet incorporé est affectée à une "cloison", qui s'exécute sur un seul thread. En d'autres termes, tous les appels à une instance d'un contrôle se produisent sur le même thread.  
  
 Toutefois, différentes instances du même type de contrôle peuvent être affectées à différentes cloisons. Par conséquent, si plusieurs instances d’un contrôle partagent des données en commun (par exemple, les données statiques ou globales), alors l’accès à ces données partagées doit être protégé par un objet de synchronisation, tel qu’une section critique.  
  
 Pour plus d’informations sur le modèle cloisonné de thread, consultez [processus et Threads](http://msdn.microsoft.com/library/windows/desktop/ms684841) dans les *référence du programmeur OLE*.  
  
## <a name="why-support-apartment-model-threading"></a>Pourquoi prendre en charge le modèle cloisonné de thread  
 Les contrôles qui prennent en charge le modèle de thread apartment peuvent être utilisés dans des applications conteneur multithread qui prennent également en charge le modèle de cloison. Si vous n'activez pas le modèle de thread apartment, vous limiterez le jeu potentiel de conteneurs dans lesquels votre contrôle peut être utilisé.  
  
 Activer le modèle de thread apartment est facile pour la plupart des contrôles, notamment s'ils ont peu ou pas de données partagées.  
  
## <a name="protecting-shared-data"></a>Protection des données partagées  
 Si votre contrôle utilise des données partagées, telles qu'une variable membre statique, l'accès à ces données doivent être protégées par une section critique pour éviter que plusieurs threads modifient les données en même temps. Pour installer une section critique à cet effet, déclarez une variable membre statique de la classe `CCriticalSection` dans la classe de votre contrôle. Utilisez le `Lock` et **Unlock** fonctions membres de cette section critique de l’objet chaque fois que votre code accède aux données partagées.  
  
 Considérons, par exemple, une classe de contrôle qui doit contenir une chaîne partagée par toutes les instances. Cette chaîne peut être maintenue dans une variable membre statique et être protégée par une section critique. La déclaration de classe du contrôle contient les éléments suivants :  
  
```  
class CSampleCtrl : public COleControl  
{  
 ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 L'implémentation de la classe comprend des définitions de ces variables :  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 L'accès au membre statique `_strShared` peut ensuite être protégé par la section critique :  
  
```  
void CSampleCtrl::SomeMethod()  
{  
    _critSect.Lock();
if (_strShared.Empty())  
    _strShared = "<text>";  
    _critSect.Unlock();

 ...  
}  
```  
  
## <a name="registering-an-apartment-model-aware-control"></a>Enregistrement d'un contrôle compatible avec le modèle apartment  
 Les contrôles qui prennent en charge le modèle de thread apartment doivent indiquer cette fonctionnalité dans le Registre, en ajoutant la valeur nommée « ThreadingModel » avec une valeur « Apartment » dans leur entrée de Registre des ID de classe sous le *id de classe* \\ **InprocServer32** clé. Pour empêcher que cette clé soit automatiquement inscrite pour votre contrôle, passez l'indicateur `afxRegApartmentThreading` dans le sixième paramètre de `AfxOleRegisterControlClass`:  
  
```  
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)  
{  
    if (bRegister)  
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(), 
    m_clsid, 
    m_lpszProgID, 
    IDS_SAMPLE, 
    IDB_SAMPLE, 
    afxRegApartmentThreading, 
    _dwSampleOleMisc, 
    _tlid, 
    _wVerMajor, 
    _wVerMinor);

 else  
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}  
```  
  
 Si votre projet de contrôle est généré par ControlWizard dans la version 4.1 de Visual C++ ou une version ultérieure, cet indicateur est déjà présent dans votre code. Aucune modification n'est nécessaire pour stocker le modèle de thread.  
  
 Si le projet a été généré par une version précédente de ControlWizard, votre code existant a une valeur booléenne comme sixième paramètre. Si le paramètre existant est TRUE, modifiez-le en `afxRegInsertable | afxRegApartmentThreading`. Si le paramètre existant est FALSE, modifiez-le en `afxRegApartmentThreading`.  
  
 Si votre contrôle ne respecte pas les règles du modèle de thread apartment, vous ne devez pas passer `afxRegApartmentThreading` dans ce paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

