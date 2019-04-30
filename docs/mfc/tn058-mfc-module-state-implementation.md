---
title: 'TN058 : Implémentation de l’état du Module MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.implementation
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: db34f528e70a7dcc437836684656b3ce8a4078fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399594"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058 : Implémentation de l’état du Module MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique décrit l’implémentation de constructions de « État du module MFC ». Est de comprendre l’implémentation du module état critique pour vous à l’aide de la bibliothèque MFC des DLL à partir d’une DLL partagées (ou un serveur in-process OLE).

Avant de lire cette note, reportez-vous à « La gestion de l’état de MFC Modules de données » dans [création de nouveaux Documents, Windows et des vues](../mfc/creating-new-documents-windows-and-views.md). Cet article contient des informations importantes sur l’utilisation et des informations générales sur ce sujet.

## <a name="overview"></a>Vue d'ensemble

Il existe trois types d’informations d’état MFC : État du module, l’état du processus et état du Thread. Parfois ces types d’état peuvent être combinées. Par exemple, les cartes de handles de MFC sont module local et thread local. Ainsi, les deux modules différents avoir des mappages différents dans chacun de leurs threads.

État du processus et l’état du Thread sont similaires. Ces éléments de données sont traditionnellement les variables globales, mais ont besoin d’être spécifiques à un processus donné ou thread pour la prise en charge Win32s appropriée ou pour la prise en charge du multithreading appropriée. Catégorie à laquelle un élément de données donné s’intègre dans dépend de cet élément et ses sémantiques souhaitées en ce qui concerne les limites de processus et de threads.

État du module est unique, car elle peut contenir réellement globale état ou état de processus local ou du thread local. En outre, il est possible rapidement.

## <a name="module-state-switching"></a>Changement d’état du module

Chaque thread contient un pointeur vers l’état du module « actuel » ou « actifs » (sans surprise, le pointeur fait partie de l’état local de thread de MFC). Ce pointeur est modifié lorsque le thread d’exécution passe une limite de module, tel qu’une application appelant dans un contrôle OLE ou DLL ou un contrôle OLE rappelle dans une application.

L’état du module actuel est basculée en appelant `AfxSetModuleState`. La plupart du temps, vous gérerez jamais directement avec l’API. MFC, dans de nombreux cas, il vous demande de (à WinMain, OLE-points d’entrée, `AfxWndProc`, etc..). Cette opération est effectuée dans n’importe quel composant que vous écrivez en liant statiquement dans une spéciale `WndProc`et une spéciale `WinMain` (ou `DllMain`) qui sait quel état du module doit être actualisé. Vous pouvez voir ce code en examinant DLLMODUL. CPP ou APPMODUL. CPP dans le répertoire MFC\SRC.

Il est rare que vous souhaitez définir l’état du module et donnez-lui la valeur de retour pas. La plupart du temps que vous voulez effectuer votre propre module de « push » d’état que celui en cours et puis, une fois que vous avez terminé, « pop » dans le contexte d’origine. Pour cela, la macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) et la classe spéciale `AFX_MAINTAIN_STATE`.

`CCmdTarget` a des fonctionnalités spéciales pour prendre en charge la commutation de module état. En particulier, un `CCmdTarget` est la classe racine utilisée pour OLE COM et OLE automation points d’entrée. Comme n’importe quel autre point d’entrée exposés au système, ces points d’entrée doivent définir l’état du module approprié. Comment est une donnée `CCmdTarget` savoir ce que l’état du module « correct » doit être la réponse est qu’il « souvient » qu’est l’état du module « actuel » lorsqu’il est construit, tel qu’il peut définir l’état du module en cours à celui « mémorisée » appelée valeur lorsqu’il est plus loin. Par conséquent, le module d’état qui une donnée `CCmdTarget` est associé l’objet est l’état du module en cours lorsque l’objet a été construit. Prendre un exemple simple de chargement d’un serveur INPROC, création d’un objet et appeler ses méthodes.

1. La DLL est chargée par OLE à l’aide de `LoadLibrary`.

2. `RawDllMain` est appelée en premier. Il définit l’état du module à l’état du module statique connu pour la DLL. Pour cette raison `RawDllMain` statiquement liée à la DLL.

1. Le constructeur de la fabrique de classe associé à notre objet est appelé. `COleObjectFactory` est dérivé de `CCmdTarget` et par conséquent, il s’en souvient dans chaque état du module, il a été instancié. Ceci est important, lorsque la fabrique de classe est invitée à créer des objets, il sait désormais quel état de module à rendre actuel.

4. `DllGetClassObject` est appelée pour obtenir la fabrique de classe. MFC recherche dans la liste de fabrique de classe associée à ce module et le retourne.

5. La méthode `COleObjectFactory::XClassFactory2::CreateInstance` est appelée. Avant de créer l’objet et retourner, cette fonction affecte l’état du module à l’état du module en cours à l’étape 3 (celui qui était en cours lorsque le `COleObjectFactory` a été instancié). Cette opération est effectuée à l’intérieur de [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Lorsque l’objet est créé, il est trop un `CCmdTarget` dérivés et de la même façon `COleObjectFactory` mémorisés quel état du module était actif, de ce fait, ce nouvel objet. Maintenant l’objet sait quel état du module pour basculer vers chaque fois qu’elle est appelée.

1. Le client appelle une fonction sur l’objet OLE COM il a reçu à partir de son `CoCreateInstance` appeler. Lorsque l’objet est appelée, elle utilise `METHOD_PROLOGUE` pour basculer l’état du module comme `COleObjectFactory` est.

Comme vous pouvez le voir, l’état du module est propagée à partir de l’objet à objet lors de leur création. Il est important de disposer de l’état du module définir de façon appropriée. Si elle n’est pas définie, votre objet DLL ou COM peut mal interagir avec une application MFC qui l’appelle, ou peut être impossible de trouver ses propres ressources ou peut échouer par d’autres moyens d’effectuer.

Notez que certains types de DLL, en particulier les DLL « Extension MFC » ne changez pas l’état du module dans leurs `RawDllMain` (en fait, ils généralement n’ont pas un `RawDllMain`). Il s’agit, car elles sont conçues pour se comporter « comme si » ils étaient effectivement présentes dans l’application qui les utilise. Ils sont très bien une partie de l’application est en cours d’exécution et il est leur intention de modifier l’état global de cette application.

Contrôles OLE et autres DLL est très différents. Ils ne souhaitent pas modifier l’état de l’application appelante ; l’application qui les appelle même peut-être pas une application MFC et par conséquent, il ne peut y avoir aucun état à modifier. Il s’agit de la raison que le changement d’état module a été inventé.

Pour des fonctions exportées à partir d’une DLL, tel que celui qui lance une boîte de dialogue dans votre DLL, vous devez ajouter le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Cela permute l’état actuel du module avec l’état retourné par [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) jusqu'à la fin de la portée actuelle.

Problèmes avec les ressources dans les DLL se produira si la macro AFX_MODULE_STATE n’est pas utilisée. Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Ce modèle est réellement enregistré dans la DLL. La cause première est que les informations sur l’état du module MFC n’ont pas été basculées par la macro AFX_MODULE_STATE. Le handle de ressources est récupéré de l'état du module MFC. Ne pas afficher l'état du module provoque l'utilisation du mauvais handle de ressource.

AFX_MODULE_STATE n’a pas besoin à placer dans chaque fonction dans la DLL. Par exemple, `InitInstance` peut être appelée par le code MFC dans l’application sans AFX_MODULE_STATE car MFC déplace automatiquement l’état du module avant `InitInstance` , puis le restaure après le retour `InitInstance` retourne. Cela vaut également pour tous les gestionnaires de messages de carte. Les DLL régulières MFC ont une procédure de fenêtre principale spéciale qui bascule automatiquement l’état du module avant d’acheminer un message.

## <a name="process-local-data"></a>Traiter les données locales

Traiter les données locales serait pas de ce type préoccupation n'avait pas été pour la difficulté du modèle Win32s DLL. Dans Win32s toutes les DLL partagent leurs données globales, même lorsque le chargement par plusieurs applications. Cela est très différent du modèle de données de DLL Win32 « réels », où chaque DLL Obtient une copie distincte de son espace de données dans chaque processus qui s’attache à la DLL. Pour ajouter à la complexité, données allouées sur le tas dans une DLL Win32s sont en fait processus spécifique (au moins autant que la propriété passe). Tenez compte des données et au code suivant :

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

Considérez que se passe-t-il si le code ci-dessus dans se trouve dans une DLL et que la DLL est chargée par deux processus A et B (il peut, en fait, être deux instances de la même application). Un appelle `SetGlobalString("Hello from A")`. Par conséquent, la mémoire est allouée pour le `CString` données dans le contexte du processus A. n’oubliez pas que le `CString` lui-même est global et est visible pour les deux A et b. B appelle maintenant `GetGlobalString(sz, sizeof(sz))`. B sera en mesure de voir les données ensemble. Il s’agit, car Win32s n’offre aucune protection entre les processus, comme le fait de Win32. C’est le premier problème ; dans de nombreux cas, il n’est pas souhaitable d’avoir une seule application affectent les données globales sont considérées comme appartenant à une autre application.

Il existe des problèmes supplémentaires. Supposons que maintenant se termine. Lorsqu’une se termine, la mémoire utilisée par le '`strGlobal`' chaîne devient disponible pour le système, autrement dit, toute la mémoire allouée par le processus A est automatiquement libérée par le système d’exploitation. Il n’est pas libéré, car le `CString` destructeur est appelé ; il n’a pas encore été appelée. Il est libéré simplement parce que l’application qui lui a été alloué a quitté la scène. Maintenant, si elle est appelée B `GetGlobalString(sz, sizeof(sz))`, il peut ne pas obtenir des données valides. D’autres applications peuvent avoir utilisé cette mémoire pour autre chose.

Il existe clairement un problème. MFC 3.x utilisé une technique appelée stockage local des threads (TLS). MFC 3.x alloue un index TLS qui sous Win32s agit comme un index de stockage local des processus, même si elle n’est pas appelée qui et serait faire référence à toutes les données en fonction de cet index TLS. Cela est similaire à l’index TLS qui a été utilisé pour stocker des données locales de thread sur Win32 (voir ci-dessous pour plus d’informations sur ce sujet). Cela a provoqué chaque DLL MFC d’utiliser au moins deux index TLS par processus. Lorsque vous compte pour le chargement de nombreux contrôle DLL OLE (OCX), vous manquer rapidement index TLS (64 uniquement sont disponibles). En outre, MFC avait placer toutes ces données au même endroit, dans une structure unique. Il n’était pas très extensible et n’était pas idéal en ce qui concerne son utilisation d’indices TLS.

MFC 4.x cela répond avec un ensemble de modèles de classe que vous pouvez « enveloppé » les données qui doivent être des processus locaux. Par exemple, le problème mentionné ci-dessus peut être résolu en écriture :

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC implémente ce en deux étapes. Tout d’abord, il existe une couche sur Win32 __Tls\*__  API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc.) qui Utilisez uniquement deux index TLS par processus, quel que soit le nombre de DLL que vous avez. Ensuite, le `CProcessLocal` modèle est fourni pour accéder à ces données. Il substitue l’opérateur -> qui est ce qui permet à la syntaxe intuitive vous voir ci-dessus. Tous les objets qui sont encapsulés par `CProcessLocal` doit être dérivé de `CNoTrackObject`. `CNoTrackObject` fournit un allocateur de niveau inférieur (**LocalAlloc**/**LocalFree**) et un destructeur virtuel telles que MFC peut détruire automatiquement les objets de processus local lorsque le processus est terminé. Ces objets peuvent avoir un destructeur personnalisé si un nettoyage supplémentaire est nécessaire. L’exemple ci-dessus ne nécessite pas un, dans la mesure où le compilateur génère un destructeur par défaut pour détruire l’embedded `CString` objet.

Il existe d’autres avantages intéressante de cette approche. Non seulement sont tous `CProcessLocal` objets détruits automatiquement, elles ne sont pas construites jusqu'à ce qu’ils sont nécessaires. `CProcessLocal::operator->` instancie l’objet associé à la première fois qu’elle est appelée et pas avant. Dans l’exemple ci-dessus, cela signifie que le «`strGlobal`' chaîne ne sera construite jusqu'à ce que la première fois `SetGlobalString` ou `GetGlobalString` est appelée. Dans certains cas, cela peut permettre de réduire les temps de démarrage DLL.

## <a name="thread-local-data"></a>Données locales de thread

Similaire à traiter des données locales, les données locales de thread sont utilisées lorsque les données doivent se trouver sur un thread donné. Autrement dit, vous devez une instance distincte des données pour chaque thread qui accède à ces données. Cela peut souvent servir à la place des mécanismes de synchronisation complète. Si les données n’a pas besoin d’être partagées par plusieurs threads, ces mécanismes peuvent être coûteux et inutile. Supposons que nous avions un `CString` objet (un peu comme l’exemple ci-dessus). On peut la rendre thread local en l’encapsulant avec un `CThreadLocal` modèle :

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

Si `MakeRandomString` a été appelée à partir de deux threads différents, chacun est « aléatoire » la chaîne de différentes façons sans interférer avec les autres. Il s’agit, car il est en fait une `strThread` instance par thread au lieu qu’une seule instance globale.

Notez comment une référence est utilisée pour capturer le `CString` adresse qu’une seule fois au lieu d’une fois par itération de boucle. Le code de la boucle ont été écrits avec `threadData->strThread` everywhere '`str`' est utilisé, mais le code serait beaucoup plus lent dans l’exécution. Il est préférable de mettre en cache une référence aux données lorsque de telles références se produisent dans des boucles.

Le `CThreadLocal` modèle de classe utilise les mêmes mécanismes que `CProcessLocal` n’et les mêmes techniques d’implémentation.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
