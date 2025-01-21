## Development

Đối với các tác vụ cơ bản, chỉ cần nhớ 3 câu lệnh cơ bản:

git add .  
git commit -m "Chore: update files"  
git push origin develop

Để tạo nhánh mới, switch nhánh sử dụng:

git checkout -b "feature/827-show-product-list"

## Pull request

Nếu đó là task: Minor: [ticket-number] - [description]  
VD: Minor: 827 - show product list

Nếu đó là bug: Patch: [ticket-number] - [description]  
VD: Patch: 828 - Product not show

## Stash

Trường hợp khá thường gặp là chúng ta code thẳng lên nhánh develop khi thực hiện một task mới. Khi nhận ra thì chúng ta phải checkout để tạo nhánh mới nhưng git yêu cầu phải commit trước khi checkout. Khi đó chỉ cần sử dụng 2 câu lệnh sau:

git stash

git stash pop

## Cherry pick

Trong các trường hợp sau khi deploy lên test site hoặc production. Nếu phát hiện ra một bug mới, ngoài việc PR vào dev branch, chúng ta cần cherry pick vào test site hoặc production. Khi đó ta sử dụng:

git cherry-pick commitSha

## Merge và rebase

Giả sửa chúng ta có nhánh develop và feature. Trong hầu hết các hợp merge sẽ được sử dụng, cách merge làm là tạo một commit merge cùng với các commit từ feature vào develop.

Rebase giúp cho lịch sử commit đẹp hơn khi thay vì tạo một merge commit, nó sẽ sắp xếp vào develop. Điều này giống như việc chúng ta cherry pick từng commit vào develop.

## Commit nhầm message

git commit --amend
