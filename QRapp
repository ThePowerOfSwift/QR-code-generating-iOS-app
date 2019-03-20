//
//  ViewController.swift
//  qrcode
//
//  Created by Nikhil Anu on 3/19/19.
//  Copyright © 2019 Nikhil Anu. All rights reserved.
//

import UIKit

class ViewController: UIViewController {
    
    var qrcodeImage: CIImage!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
    }
    
    
    
    func displayQRCodeImage() {
        let scaleX = imgQRCode.frame.size.width / qrcodeImage.extent.size.width
        let scaleY = imgQRCode.frame.size.height / qrcodeImage.extent.size.height
        
        let transformedImage = qrcodeImage.transformed(by: CGAffineTransform(scaleX: scaleX, y: scaleY))
        
        imgQRCode.image = UIImage(ciImage: transformedImage)
        
    }
    
    @IBOutlet weak var textField: UITextField!
    
    @IBOutlet weak var imgQRCode: UIImageView!
    
    @IBOutlet weak var btnAction: UIButton!
    
  
    
    @IBAction func performButtonAction(_ sender: Any) {
        if qrcodeImage == nil {
            if textField.text == "" {
                return
            }
            let data = textField.text?.data(using: String.Encoding.isoLatin1, allowLossyConversion: false)
            
            let filter = CIFilter(name: "CIQRCodeGenerator")
            
            filter?.setValue(data, forKey: "inputMessage")
            filter?.setValue("Q", forKey: "inputCorrectionLevel")
            
            qrcodeImage = filter?.outputImage
            
            displayQRCodeImage()
            
            textField.resignFirstResponder()
            
            
            btnAction.setTitle("Clear", for: UIControl.State.normal)
            //slider.isHidden = false
        }
        else {
            imgQRCode.image = nil
            qrcodeImage = nil
            btnAction.setTitle("Generate", for: UIControl.State.normal)
        }
    }


}
