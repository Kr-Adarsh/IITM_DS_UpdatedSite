let apiKey = "AIzaSyBooYHYxSM6QB4i7m-BjHZfPD_-3J2zmTE";
let sheetName = "Sheet1";
let updates = [];
function indexPage() {
  let sheetId = "1fJATUKhgELLjNDAq0gFzQvDZjtNCObhibkyIPBtbhhY";
  let url =
    "https://sheets.googleapis.com/v4/spreadsheets/" +
    sheetId +
    "/values/" +
    sheetName +
    "?alt=json&key=" +
    apiKey;

  $.ajax({
    url: url,
    type: "GET",
    dataType: "jsonp",
    cors: true,
    contentType: "application/json",
    secure: true,
    headers: {
      "Access-Control-Allow-Origin": "*",
    },
    success: function (data) {
      let sheetData = data.values ? data.values : [];
      for (i = 1; i < sheetData.length; i++) {
        let obj = {
          text: sheetData[i][0] ? sheetData[i][0] : "",
          ref: sheetData[i][1] ? sheetData[i][1] : "",
          date: sheetData[i][2] ? sheetData[i][2] : "",
          view: sheetData[i][3] ? sheetData[i][3] : "",
          content_type: sheetData[i][4] ? sheetData[i][4] : "",
        };
        updates.push(obj);
      }
      dynamicAnnouncements("latest-updates-items", "");
    },
  });
  function dynamicAnnouncements(id, type) {
    let parent = document.getElementById(id);
    parent.innerHTML = "";

    updates.forEach((element) => {
      if (element.view === "No" && !type) return;

      let bulletIcon = `<span class="mr-2">
              <i class="fas fa-bullseye"></i>
            </span>`;

      if (element.content_type) bulletIcon = ``;

      // Paragraph tag
      let p = document.createElement("p");
      p.className = "latest-updates-item text-dark";
      p.innerHTML = element.text;

      if (element.ref !== "") {
        let anchorWord = "";
        let startIndex = element.text.indexOf("[");
        let lastIndex = element.text.indexOf("]");
        for (let i = startIndex + 1; i < lastIndex; i++) {
          anchorWord = anchorWord + element.text[i];
        }
        let tempWrod = "[" + anchorWord + "]";
        p.innerHTML =
          bulletIcon +
          element.text.replace(
            tempWrod,
            ` <a href="${element.ref}">${anchorWord}</a> `
          );
      }

      // Span tag
      if (element.date) {
        let span = document.createElement("span");
        span.className = "badge badge-secondary latest-updates-bedge ml-1";
        span.innerHTML = element.date;

        // Final paragraph
        p.appendChild(span);
      }
      parent.appendChild(p);
    });
  }
}

function archivePage() {
  let sheetId = "1bf2O44DBJdHOQHvm43kvoUtmmOnDpVwOsI7oBVS3NzA";
  let url =
    "https://sheets.googleapis.com/v4/spreadsheets/" +
    sheetId +
    "/values/" +
    sheetName +
    "?alt=json&key=" +
    apiKey;

  $.getJSON(url, function (data) {
    let sheetData = data.values ? data.values : [];
    sheetData.forEach((element) => {
      if (element && element.length) {
        let date = element[0];
        let description = element[1];
        let link = element[2];
        document.getElementById("archive").innerHTML +=
          "<tr>" +
          '<td  style="padding-left: 0;">' +
          date +
          "</td>" +
          "<td>" +
          description +
          "</td>" +
          '<td><a target="_blank" href="' +
          link +
          '">View File <i class="fa fa-external-link" aria-hidden="true"></i></a></td>' +
          "</tr>";
      }
    });
  });
  d;
}

function eventsPage() {
  let sheetOneId = "1m3T80A_RkR1yab0Hadkbg7CJhB47BwhXahhNLaOECDQ";
  let urlOne =
    "https://sheets.googleapis.com/v4/spreadsheets/" +
    sheetOneId +
    "/values/" +
    sheetName +
    "?alt=json&key=" +
    apiKey;
  $.getJSON(urlOne, function (data) {
    let sheetData = data.values ? data.values : [];
    if (!sheetData) {
      document.getElementById("upcoming_thead").style.display = "none";
      document.getElementById("upcoming_status").innerHTML =
        "- No upcoming events at the moment.";
      return;
    }
    sheetData.forEach((element) => {
      if (element && element.length) {
        let date = element[0];
        let event = element[1];
        let link = element[2];

        let html = `<div class="my-6 py-3 bg-light row" style="height: auto;">
                    <div class="col-12 col-sm-6" style="height:auto">
                        <div class="videoContainer">
                            <div class="landingVideoCourse">
                                <iframe width="560" height="415" src="${link}" frameborder="0"
                                    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                                    allowfullscreen></iframe>
                            </div>
                        </div>
                    </div>
                    <div class="col-12 col-sm-6 p-4">
                        <p class="display-4 text-dark">${date}</p>
                        <p class="text-dark">${event}</p>
                    </div>
                </div>`;

        if (!link || !date || !event) {
          html = "";
        }
        document.getElementById("upcoming_events").innerHTML += html;

        // document.getElementById('upcoming_events').innerHTML += ('<tr>' + '<td  style="padding-left: 0;">' + date + '</td>' + '<td>' + event + '</td>' + '<td><a target="_blank" href="' + link + '">View <i class="fa fa-external-link" aria-hidden="true"></i></a></td>' + '</tr>');
      }
    });
  });

  let sheetTwoId = "1cFkaPiBUSspr-9eRFXekYp3QhwKgcpjfkcxViSPpc3Y";
  let urlTwo =
    "https://sheets.googleapis.com/v4/spreadsheets/" +
    sheetTwoId +
    "/values/" +
    sheetName +
    "?alt=json&key=" +
    apiKey;
  $.getJSON(urlTwo, function (data) {
    let sheetData = data.values ? data.values : [];
    if (!sheetData || sheetData.length == 0) {
      document.getElementById("past_thead").style.display = "none";
      document.getElementById("past_events").innerHTML =
        "<tr><td colspan=3><p>No past events at the moment.</p></td></tr>";
      return;
    }

    sheetData.forEach((element) => {
      if (element && element.length) {
        let date = element[0];
        let event = element[1];
        let link = element[2];

        let html = `<div class="my-6 py-3 bg-light row" style="height: auto;">
                    <div class="col-12 col-sm-6">
                        <div class="videoContainer">
                            <div class="landingVideoCourse">
                                <iframe width="560" height="315" src="${link}" frameborder="0"
                                    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                                    allowfullscreen></iframe>
                            </div>
                        </div>
                    </div>
                    <div class="col-12 col-sm-6 p-4">
                        <p class="display-4 text-dark">${date}</p>
                        <p class="text-dark">${event}</p>
                    </div>
                </div>`;
        if (!link || !date || !event) {
          html = "";
        }
        document.getElementById("past_events").innerHTML += html;
        // document.getElementById('past_events').innerHTML += ('<tr>' + '<td  style="padding-left: 0;">' + date + '</td>' + '<td>' + event + '</td>' + '<td><a target="_blank" href="' + link + '">View <i class="fa fa-external-link" aria-hidden="true"></i></a></td>' + '</tr>');
      }
    });
  });
}

function helpVideo() {
  let sheetId = "11ERj7zfsn87vAsaEiC6AUrOzbO-Ctn7HOiIOSyWNLMA";
  let url =
    "https://sheets.googleapis.com/v4/spreadsheets/" +
    sheetId +
    "/values/" +
    sheetName +
    "?alt=json&key=" +
    apiKey;

  $.getJSON(url, function (data) {
    let sheetData = data.values ? data.values : [];
    sheetData.forEach((element) => {
      if (element && element.length) {
        let title = element[0];
        let channel = element[1];
        let link = element[2];
        document.getElementById("upcoming_events").innerHTML +=
          "<tr>" +
          '<td  style="padding-left: 0;"><a target="_blank" href="' +
          link +
          '">' +
          title +
          '&nbsp;<i class="fa fa-external-link" aria-hidden="true"></i></a></td>' +
          '<td   style="padding-right: 0;"><i>' +
          channel +
          "</i></td>" +
          "<td>" +
          "</tr>";
      }
    });
  });
}

function inTheMedia() {
  let sheetId = "11ERj7zfsn87vAsaEiC6AUrOzbO-Ctn7HOiIOSyWNLMA";
  let url =
    "https://sheets.googleapis.com/v4/spreadsheets/" +
    sheetId +
    "/values/" +
    sheetName +
    "?alt=json&key=" +
    apiKey;

  $.getJSON(url, function (data) {
    let sheetData = data.values ? data.values : [];
    sheetData.forEach((element) => {
      if (element && element.length) {
        let title = element[0];
        let channel = element[1];
        let link = element[2];
        document.getElementById("inthemedia").innerHTML +=
          "<tr>" +
          '<td  style="padding-left: 0;"><a target="_blank" href="' +
          link +
          '">' +
          title +
          '&nbsp;<i class="fa fa-external-link" aria-hidden="true"></i></a></td>' +
          '<td   style="padding-right: 0;"><i>' +
          channel +
          "</i></td>" +
          "<td>" +
          "</tr>";
      }
    });
  });
}
