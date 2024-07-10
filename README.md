# Slide-div-for-time-set
slide for div time set for hide and show
<%@ page language="C#" autoeventwireup="true" codefile="InformationDashboard.aspx.cs" inherits="Production_informationDashboard" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <link href="../Content/style.css" rel="stylesheet" media="screen" />
    <link href="../Content/font-awesome.css" rel="stylesheet" />
    <link href="../Content/bootstrap.css" rel="stylesheet" />
    <link href="../Content/bootstrap.min.css" rel="stylesheet" />
    <script src="../Scripts/jquery.min.js"></script>
   
</head>
<body>

    <form id="form1" runat="server">


            <div class="col-md-12 col-lg-12" id="a">
              <table  class="table table-bordered table-responsive table-sm" style="width: 100%!important; overflow: scroll;">
                    <thead>
                        <tr>
                            <th>Start</th>
                            <th>Services</th>
                            <th>Process</th>
                        </tr>
                    </thead>
                </table>
            </div>

            <div class="col-md-12" id="b">
                <table  class="table table-bordered table-responsive table-sm" style="width: 100%!important; overflow: scroll;">
                    <thead>
                        <tr>
                            <th>STAGE</th>
                            <th>Production</th>
                            <th>Transfer</th>
                        </tr>
                    </thead>
                </table>
            </div>
            <div class="col-md-12" id="c">                
                   <table  class="table table-bordered table-responsive table-sm" style="width: 100%!important; overflow: scroll">
                       <thead>
                          <tr>
                                <th>DELIVERY LOCATION</th>
                               <th>Delay Count</th>
                               <th>Count</th>
                          </tr>
                      </thead>
                 </table>
            </div>


        

        <script>

         //////  Dropdown click show and hide ///////

            $(document).ready(function () {
                // Function to toggle visibility of div elements based on dropdown selection
                $("#Select1").change(function () {
                    var selectedValue = $(this).val();
                    if (selectedValue == "1") {
                        $("#a").show();
                        $("#b").hide();
                        $("#c").hide();
                    } else if (selectedValue == "2") {
                        $("#a").hide();
                        $("#b").show();
                        $("#c").hide();
                    } else if (selectedValue == "3") {
                        $("#a").hide();
                        $("#b").hide();
                        $("#c").show();
                    } else {
                        $("#a").hide();
                        $("#b").hide();
                        $("#c").hide();
                    }
                });

                // Initially hide all divs
                $("#a").hide();
                $("#b").hide();
                $("#c").hide();

            });

            ///////////////  slide for timeings   ////////////////

            $(document).ready(function () {
                function showDivA() {
                    $("#a").show();
                    $("#b").hide();
                    $("#c").hide();
                    setTimeout(hideDivA, 15 * 60 * 1000); // Hide div a after 15 minutes
                }

                function hideDivA() {
                    $("#a").hide();
                    $("#b").show();
                    $("#c").hide();
                    setTimeout(showDivC, 15 * 60 * 1000); // Show div b after 15 minutes
                }

                function showDivC() {
                    $("#a").hide();
                    $("#b").hide();
                    $("#c").show();
                    setTimeout(hideDivC, 15 * 60 * 1000); // Hide div c after 15 minutes
                }

                function hideDivC() {
                    $("#a").show();
                    $("#b").hide();
                    $("#c").hide();
                    setTimeout(hideDivA, 15 * 60 * 1000); // Show div a after 15 minutes
                }

                showDivA();
            });



            /////// scroll auto timing ////////
            
            function scrollUp() {
                $('html, body').animate({ scrollTop: 0 }, 5000, function () {
                    setTimeout(scrollDown, 1000);
                });
            }
           function scrollDown() {
               $('html, body').animate({ scrollTop: $(document).height() }, 5000, function () {                   
                    setTimeout(scrollUp, 1000);
                });
            }


        </script>

    </form>
</body>
</html>
