# Dockerfile-Problem

#ENG
If you think you have written your Dockerfile correctly but it does not work, you can try this method.
Under normal circumstances, when you want to write the dockerfile file, you will see such a writing style in various sources.

FROM python:3.9

COPY . /app
WORKDIR /app

RUN pip install -r requirements.txt

ENTRYPOINT ["python", "app.py"]


I was using this in my project at first. After dockerizing the project, I was deploying it to Azure, but it was not working. There was no problem working locally. Then, I changed the from section in the code as follows. When you test the application after deploying it to Azure, it may not work immediately. If you wait approximately 5-10 minutes, you will see that it works without any problems.


FROM amd64/python:3.9-buster

COPY . /app
WORKDIR /app

# Install the required dependencies
RUN pip install -r requirements.txt

ENTRYPOINT ["python", "app.py"]


#TR
Dockerfile’ınızı doğru yazdığınızı ancak işe yaramadığını düşünüyorsanız bu yöntemi deneyebilirsiniz.
Normal şartlarda dockerfile dosyasını yazmak istediğinizde çeşitli kaynaklarda böyle bir yazım şekli olduğunu görürsünüz.

FROM python:3.9

COPY . /app
WORKDIR /app

RUN pip install -r requirements.txt

ENTRYPOINT ["python", "app.py"]


Ben de ilk başta projemde bunu kullanıyordum. Projeyi dockerize ettikten sonra azureye deploy ediyordum ama çalışmıyordu. Localde çalışmasında hiç bir sorun yoktu. Daha sonrasında koddaki from kısmınnı aşağıdaki gibi değiştirdim. Uygulamayı azureye deploy ettikten sonra test ettiğinizde hemen çalışmayabilir. Yakllaşık olarak 5-10 dakika beklerseniz sorunsuz çalıştığını göreceksiniz.


FROM amd64/python:3.9-buster

COPY . /app
WORKDIR /app

# Gerekli bağımlılıkları kurun
RUN pip install -r requirements.txt

ENTRYPOINT ["python", "app.py"] 
