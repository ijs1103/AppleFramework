# AppleFramework

![Simulator Screen Recording - iPod touch (7th generation) - 2023-01-13 at 15 44 49](https://user-images.githubusercontent.com/42196410/212255362-7c554123-e6cf-4735-aae2-411a22787da3.gif)



## 🧩 개요

- `CompositionalLayout`으로 column이 3개인 그리드뷰 표시.

- 디테일뷰 모달로 띄우기.

- Learn More 버튼탭시 사파리창 띄우기.

## 🤔 배운 내용

### ✔️ 모달 띄우기

1) 컬렉션뷰의 뷰컨트롤러에서 `UICollectionViewDelegate` 프로토콜 채택 후 `didSelectItemAt`메서드 구현.

2) 모달창의 뷰컨트롤러(`FrameworkDetailViewController`)에 데이터를 넘겨주고 `present` 한다.

```
extension FrameworkListViewController: UICollectionViewDelegate {
    func collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath) {
        let framework = list[indexPath.item]
        print(">>> selected: \(framework.name)")
        
        let sb = UIStoryboard(name: "Detail", bundle: nil)
        let vc = sb.instantiateViewController(withIdentifier: "FrameworkDetailViewController") as! FrameworkDetailViewController
        vc.framework = framework
        
        present(vc, animated: true)
    }
}

```
### ✔️ 사파리창 띄우기

`SafariServices`를 import하고 `SFSafariViewController`에 URL 구조체를 넘겨준뒤, `present` 한다.

```
import SafariServices

let safari = SFSafariViewController(url: url)
        
present(safari, animated: true)

```

