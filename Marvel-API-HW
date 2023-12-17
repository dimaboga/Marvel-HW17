import UIKit
import CryptoKit

func getData(urlRequest: String) {
    let urlRequest = URL(string: urlRequest)
    guard let url = urlRequest else { return }
    URLSession.shared.dataTask(with: url) { data, response, error in
        if error != nil {
            print("Error: \(String(describing: error?.localizedDescription))")
        } else if let response = response as? HTTPURLResponse, response.statusCode == 200 {
            print("Debug: response is = \(response.statusCode)")
            guard let data = data else { return }
            let dataAsString = String(data: data, encoding: .utf8)
            print(dataAsString ?? "data doesn't exist")
        }
    }.resume()
}
func MD5(string: String) -> String {
    let digest = Insecure.MD5.hash(data: Data(string.utf8))

    return digest.map {
        String(format: "%02hhx", $0)
    }.joined()
}

let publicKey = "2ddf22236ef582e833a033fcf9b728e8"
let privateKey = "58383c3212c0d25c71d0cb93c331558bf5766774"

let ts =  "1"
let hash = MD5(string: ts + privateKey + publicKey)
let urlComics = "https://gateway.marvel.com/v1/public/comics/8450?ts=" + ts + "&apikey=" + publicKey + "&hash=" + hash

getData(urlRequest: urlComics)


